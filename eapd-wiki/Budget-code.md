This page serves to ease the learning curve for working on the budget code or as a quick reference.

It should _complement_ the documentation that exists in code. Continue to use in-code documentation as much as possible!

Use this in combination with [MMIS Budget Calculations](https://github.com/Enterprise-CMCS/eAPD/wiki/MMIS-Budget-Calculations) and [HITECH Budget Calculations](https://github.com/Enterprise-CMCS/eAPD/wiki/HITECH-Budget-Calculations).

# Terminology
* Funding source
  * HITECH
    * `hit`, `hie`, `mmisByFFP`
  * MMIS
    * `mmis` - since the whole of the MMIS APD is basically its own funding source (sorta), this field calculates the entire APD (unlike HITECH, which calculates the funding sources using only relevant parts of the APD). **Note:** This field may become obsolete in the future.
* Funding category
  * HITECH
    * N/A
  * MMIS
    * `ddi`, `mando`
* Cost category - things that cost money and will require funding to pay for
  * `contractors`, `expenses`, `statePersonnel`, `keyStatePersonnel`
* Shares
  * The APD's costs are likely going to be funded from different places. The "share" is the amount each is responsible for.
    * Federal
    * State
    * Medicaid
    * Other funding
* Fed-State split
  * The share percentage that federal and state are covering, in that order
    * ex. 90-10 means fed covers 90 percent and state covers 10 percent

# Base info
* Budget objects exist in the database for each APD _(see [/api/models](https://github.com/Enterprise-CMCS/eAPD/tree/main/api/models))_
  * We use [mongoose](https://mongoosejs.com/docs/) to define model schemas
  * There is a generic [budget model](https://github.com/Enterprise-CMCS/eAPD/blob/main/api/models/budget.js) which consists of overlapping fields between the budgets of all APD types
  * Specific models ([hitechBudget](https://github.com/Enterprise-CMCS/eAPD/blob/main/api/models/hitechBudget.js), [mmisBudget](https://github.com/Enterprise-CMCS/eAPD/blob/main/api/models/mmisBudget.js)) extend the generic budget model
* During APD creation, the budget object is created and saved in the database
* During APD update, the entire budget object is re-created then _replaces_ the existing budget in the database

# Budget calculation
_(see [/common/utils/budget.js](https://github.com/Enterprise-CMCS/eAPD/blob/main/common/utils/budget.js))_
## Initial phase
* Builds out a budget object with the correct structure _(must match the model schema)_ and zeroed out values
* The budget object is built out via multiple functions following the naming convention `default…Object`
## Calculation phase
_To get an understanding of the actual calculations and how the numbers work, see [MMIS Budget Calculations](https://github.com/Enterprise-CMCS/eAPD/wiki/MMIS-Budget-Calculations) and [HITECH Budget Calculations](https://github.com/Enterprise-CMCS/eAPD/wiki/HITECH-Budget-Calculations)._

A lot of functions and variables already exist to calculate intermediary amounts and percentages. Try to take advantage of these when possible.

The following breakdown of a few functions/variables should help gain context of the process the code follows to do the calculations.
* Key state personnel calculations
  * `addKeyStatePeronnel()` (used by MMIS)
    * Adds values to all `budget.combined` fields _(The highest level combined field)_
    * Adds values to all `budget.mmis.combined` fields
    * Add values to all `budget.mmis.keyStatePersonnel` fields
  * `updateStatePersonnel()` (used by HITECH)
* `activityTotals` - calculated via `sumActivityTotals()`
  * Useful for
    * **activity cost for the [cost categories](#terminology)**
    * **total activity cost**
    * **amount of other funding**
* `totalMedicaidCost`
  * Useful for **costs that medicaid has to cover** (activity total less other funding)
* `totalMedicaidCostShares`
  * Useful for **costs that medicaid has to cover split between federal/state** (total medicaid cost split between federal and state based on [fed-state split](#terminology))
* `costCategoryShare` - calculated via `calculateShareCostsByCategory()`
  * Useful for getting the **amounts for each cost category**
  * i.e. How much of the total medicaid cost goes to each [cost category](#terminology)
* `sumShareCosts()` (used by HITECH)
  * Adds the costs for medicaid, federal, state of an activity for a year
  * Populates budget fields: `hit`, `hie`, `mmisByFFP`
* `sumTotalCostsByCategory()` - sums total costs for an activity across all years
  * Adds values to `budget.combined.year.total` for all years
  * Adds values to `budget.combined.total.total`
  * Adds values to all `budget.mmis` total fields _(except keyStatePersonnel)_
* `sumShareCostsForFundingSource()`
  * Adds values to `budget.combined`’s nested federal, state, & medicaid keys under each year and total key
  * Adds values to all `budget.mmis` non-total fields _(ignoring keyStatePersonnel)_
* `sumShareCostsForFundingCategory()`
  * Fully populates funding category fields (`budget.ddi`, `budget.mando`)
