The MMIS APD budget calculations are a little complicated, mostly because of the repetition. This document will walk through all the numbers that are calculated, where they come from, and where they show up in the eAPD.

<details open>
<summary><h2>User inputs</h2></summary>

All of the calculations begin with user inputs.


### APD Key State Personnel

The first budget-related user input is related to APD Key State Personnel. If key personnel have costs that are directly attributable to the project(s) addressed by the APD, their costs are entered for each federal fiscal year by Full Time Equivalent (FTE) allocation and Medicaid Share(%) covered by the APD.

**Example:** For an APD that covers FFY 2023 and 2024, the state has identified three key personnel. Only two of them have costs that are directly attributable to the APD.

|Key Personnel|Has costs|FFY 2023 Cost with benefits|FFY 2023 FTE Allocation|FFY 2023 Medicaid Share (%)|FFY 2023 match rate|
|-------------|:-------:|---------------------------|-----------------------|---------------------------|-------------------|
| Amber       | Yes     | $24,000                   | 1                     |50                         |90/10 DDI          |
| Bob         | Yes     | $19,000                   | 0.5                   |100                        |90/10 DDI          |
| Caitlin     | No      |                           |                       |                           |                   |

|Key Personnel|Has costs|FFY 2024 Cost with benefits|FFY 2024 FTE Allocation|FFY 2024 Medicaid Share (%)|FFY 2024 match rate|
|-------------|:-------:|---------------------------|-----------------------|---------------------------|-------------------|
| Amber       | Yes     | $32,000                   | 0.25                  |50                         |75/25 M&O          |
| Bob         | Yes     | $22,000                   | 1                     |100                        |75/25 M&O          |
| Caitlin     | No      |                           |                       |                           |                   |

Key State Personnel are the only APD-level user-input that is incorporated into the APD budget. All other user-inputs are inside activities. The Key State Personnel are displayed above the other Activity level calculations. Key State Personnel are also the only cost that has an individual match rate. A Key State Personnel can be attributed to a 90/10 DDI or 75/25 Operations match rate. Key State Personnel also have an individual Medicaid share percent and their Medicaid cost is not determined by the Activity-level total costs or other funding.


### Activity state staff costs

Each activity can contain a list of state personnel who will be working on that activity. These state staff are not individuals but rather roles (e.g., "project assistant"). For each state staff role, the role's ***total*** costs (salary + benefits), are entered for each federal fiscal year. Then, their FTEs attributable to the activity are also entered for each fiscal year. Finally, their cost attributable to the activity is calculated by multiplying the total cost by the FTEs.

**Example:** For an APD covering FFY 2023 and 2024, the state has identified two state personnel.

|Personnel title    |Total Costs|FTE  |Activity Cost|
|-------------------|-----------|-----|-------------|
| Project assistant |           |     |             |
| --- FFY 2023      | $95,000   | 0.7 | $66,500*    |
| --- FFY 2024      | $98,500   | 1   | $98,500*    |
| Accountant II     |           |     |             |
| --- FFY 2023      | $112,000  | 2   | $224,000*   |
| --- FFY 2024      | $114,500  | 3   | $343,500*   |

\* indicates a calculated value


### Activity state non-personnel costs

Each activity can include a list of non-personnel costs for things like equipment and supplies purchases, travel costs, or training and outreach. These costs are entered for each federal fiscal year covered by the APD.

**Example:** For an APD covering FFY 2023 and 2024, the state has identified three non-personnel costs.

|Cost category|FFY 2023 Cost|FFY 2024 Cost|
|-------------|-------------|-------------|
| Training    | $40,000     | $30,000     |
| Travel      | $22,000     | $19,000     |
| Misc        | $5,000      | $6,000      |


### Activity contractor resource costs

Each activity can include a list of private contractor resources. Each contractor will either have an estimated cost per federal fiscal year, or will be an hourly resource. In either case, the costs will be entered. For hourly resources, the total cost per federal fiscal year will be calculated.

**Example:** For an APD covering FFY 2023 and 2024, the state has identified two contractor resource costs.

|Contractor   |Hourly?|Hourly rate|Hours  |FFY Cost   |
|-------------|:-----:|-----------|-------|-----------|
| ACME        | No    |           |       |           |
| -- FFY 2023 |       |           |       | $230,000  |
| -- FFY 2024 |       |           |       | $180,000  |
| LexCorp     | Yes   |           |       |           |
| -- FFY 2023 |       | $300      | 2,000 | $600,000* |
| -- FFY 2024 |       | $310      | 1,000 | $310,000* |

\* indicates a calculated value


### Other funding

Each activity can be supported by other funding sources. Those must be reported as they affect how much of the total activity cost is to be borne by Medicaid. These other funding amounts are entered for each federal fiscal year covered by the APD.

**Example:** For an APD covering FFY 2023 and 2024, the state provides the following other funding amounts:

|FFY 2023|FFY 2024|
|--------|--------|
| $5,000 | $0     |

### Match rate

Each activity is assigned a match rate that is made up of a funding category; Design, Development, and Installation (DDI) or Maintenance & Operations (M&O); and a Federal/State split percentage. Each federal fiscal year can have a different match rate depending on the type of the work being performed in this activity for the federal fiscal year. The match rate options are 90/10 DDI, 75/25 DDI, 50/50 DDI, 75/25 M&O, and 50/50 M&O.

**Example:** For an APD covering FFY 2023 and 2024, the state identifies the following funding splits:

|                  |FFY 2023|FFY 2024|
|------------------|--------|--------|
| Federal          | 90%    | 75%    |
| State            | 10%    | 25%    |
| Funding category | DDI    | M&O    |

### Summary of user inputs

- **APD Key State Personnel** - one input per personnel with costs, medicaid costs, and match rate per federal fiscal year
- **Activity** - one set of all following inputs per activity
  - **State personnel** - two inputs per role with costs per federal fiscal year
  - **Non-personnel costs** - one input per cost with costs per federal fiscal year
  - **Contractor resources** - two or three inputs per resource with costs per federal fiscal year
  - **Match rate** - one input per federal fiscal year

</details>

<details open>
<summary><h2>Calculated values</h2></summary>

There are a lot of values that get calculated, and some of them are a little bit complicated. With one exception all of the calculations are based on values from the activities. The one exception is the Key State Personnel. For Key State Personnel we first calculate the totals by year by person. The totals are: 
|                           | Math                                                                  |
|---------------------------|-----------------------------------------------------------------------|
| Total                     | `Cost with benefits` x `FTE`                                          |
| Medicaid Computable Total | `Cost with benefits` x `FTE` x `Medicaid Share %`                     | 
| Federal Share             | `Cost with benefits` x `FTE` x `Medicaid Share %` x `Federal Share %` |
| State Share               | `Cost with benefits` x `FTE` x `Medicaid Share %` x `State Share %`   |

**Example:** This example is based on the above values in the example in user inputs.
|Key Personnel|2023 Total Cost|2023 Total Computable Medicaid|2023 Federal Share|2023 State Share|
|-------------|---------------|------------------------------|------------------|----------------|
| Amber       | $24,000       | $12,000                      | $10,800          | $1,200         |
| Bob         | $9,500        | $9,500                       | $8,550           | $950           |
| Caitlin     | $0            | $0                           | $0               | $0             |

|Key Personnel|2024 Total Cost|2024 Total Computable Medicaid|2024 Federal Share|2024 State Share|
|-------------|---------------|------------------------------|------------------|----------------|
| Amber       | $8,000        | $4,000                       | $3,000           | $1,000         |
| Bob         | $22,000       | $22,000                      | $16,500          | $5,500         |
| Caitlin     | $0            | $0                           | $0               | $0             |


These values are added to the budget _prior to_ the calculations in the activities.

For the activities we first create a set of calculated values that are intermediary – necessary for later calculations, but not the final numbers presented anywhere.


### Intermediary values

- **Activity state personnel cost per fiscal year** - calculated from the state personnel ***total*** cost and FTEs. This value is displayed live while the user is entering total cost and FTE values.
**Example:** This example is based on the Program Administration activity in a HITECH APD, so it also includes the Key personnel values.

|State Personnel    |FFY 2023      |FFY 2024      |Total         |
|-------------------|--------------|--------------|--------------|
| Amber             | `   $24,000` | `   $32,000` | `   $56,000` |
| Bob               | `+  $19,000` | `+  $22,000` | `+  $41,000` |
| Project assistant | `+  $66,500` | `+  $98,500` | `+ $165,000` |
| Accountant II     | `+ $224,000` | `+ $343,500` | `+ $567,500` |
| **Total**         | `= $333,500` | `= $604,000` | `= $829,500` |

- **Activity state non-personnel cost per fiscal year** - calculated from the state non-personnel ***total*** cost. This value is displayed live while the user is entering total cost.

**Example:**

|Non-personnel |FFY 2023     |FFY 2024     |Total         |
|--------------|-------------|-------------|--------------|
| Training     | `  $40,000` | `  $30,000` | `   $70,000` |
| Travel       | `+ $22,000` | `+ $19,000` | `+  $42,000` |
| Misc         | `+  $5,000` | `+  $6,000` | `+  $11,000` |
| **Total**    | `= $67,000` | `= $55,000` | `= $123,000` |

- **Activity contractor costs per fiscal year** - for contractor resources that are hourly, calculated from the hourly rate and the number of hours. This is displayed live while the user is entering the hourly rate and number of hours.

**Example:**

| Contractor |FFY 2023      | FFY 2024     | Total         |
|------------|--------------|--------------|---------------|
| ACME       | `  $230,000` | `  $180,000` | `   $410,000` |
| LexCorp    | `+ $600,000` | `+ $310,000` | `+  $910,000` |
| **Total**  | `= $830,000` | `= $490,000` | `= $1320,000` |

### Activity costs

- **Activity total cost per fiscal year** - the sum of all activity [state personnel](#activity-state-staff-costs), [non-personnel](#activity-state-non-personnel-costs), and [contractor resource](#activity-contractor-resource-costs) costs for the fiscal year

  | FFY  | Math                            | Activity total |
  |------|---------------------------------|----------------|
  | 2023 | `$333,500 + $67,000 + $830,000` | `$1,230,500`   |
  | 2024 | `$604,000 + $55,000 + $490,000` | `$1,149,000`   |

- **Activity Medicaid total cost per fiscal year** - the activity total cost minus any [other funding](#other-funding) amount for the fiscal year

  | FFY  | Math                  | Activity Medicaid total |
  |------|-----------------------|-------------------------|
  | 2023 | `$1,230,500 - $5,000` | `$1,225,500`            |
  | 2024 | `$1,149,000 - 0`      | `$1,149,000`            |

- **Activity federal share per fiscal year** - the Medicaid total multiplied by the federal share percentage from the [federal/state split](#activity-federalstate-split) for the fiscal year

  | FFY  | Math               | Activity federal share |
  |------|--------------------|------------------------|
  | 2023 | `$1,225,500 * 90%` | `$1,102,950`           |
  | 2024 | `$1,149,000 * 75%` | `$861,750`             | 

- **Activity state share per fiscal year** - the Medicaid total multiplied by the state share percentage from the [federal/state split](#activity-federalstate-split) for the fiscal year

  | FFY  | Math               | Activity state share |
  |------|--------------------|----------------------|
  | 2023 | `$1,225,500 * 10%` | `$122,550`           |
  | 2024 | `$1,149,000 * 25%` | `$287,250`           |

There are some additional intermediary values that are necessary for future calculations and are based on activity-per-fiscal year values, so those are calculated here:

- **State personnel proportion** - this is the proportion of the **activity total cost** for the fiscal year that is made up by state personnel costs.

  | FFY  | Math                         | State personnel proportion |
  |------|------------------------------|----------------------------|
  | 2023 | `$333,500/$1,230,500 = 0.27` | 27%                        |
  | 2024 | `$604,000/$1,149,000 = 0.52` | 52%                        | 

- **Non-personnel proportion** - this is the proportion of the **activity total cost** for the fiscal year that is made up by non-personnel costs.

  | FFY  | Math                        | Non-personnel proportion |
  |------|-----------------------------|--------------------------|
  | 2023 | `$67,000/$1,230,500 = 0.05` | 5%                       |
  | 2024 | `$55,000/$1,149,000 = 0.05` | 5%                       |

- **Contractor resources proportion** - this is the proportion of the **activity total cost** for the fiscal year that is made up by contractor resources costs.

  | FFY  | Math                         | Contractor resources proportion |
  |------|------------------------------|---------------------------------|
  | 2023 | `$830,000/$1,230,500 = 0.68` | 68%                             |
  | 2024 | `$490,000/$1,149,000 = 0.43` | 43%                             |



**Example:**
|FFY 2023         |Federal share                      | State share                    |
|-----------------|-----------------------------------|--------------------------------|
| State personnel | `$1,102,950 × 27% = ` $297,796.50 | `$122,550 × 27% = ` $33,088.50 |
| Non-personnel   | `$1,102,950 ×  5% = ` $55,147.50  | `$122,550 ×  5% = ` $6,127.50  |
| Contractor      | `$1,102,950 × 68% = ` $750,006    | `$122,550 × 68% = ` $83,334    |


|FFY 2024         |Federal share math               |State share                      |
|-----------------|---------------------------------|---------------------------------|
| State personnel | `$861,750 × 52% = ` $448,110    | `$287,250 × 52% = ` $149,370    |
| Non-personnel   | `$861,750 ×  5% = ` $43,087.50  | `$287,250 ×  5% = ` $14,362.50  |
| Contractor      | `$861,750 × 43% = ` $370,552.50 | `$287,250 × 43% = ` $123,517.50 |


What are those numbers for? They seem a little out of the blue. In order to understand how much the state and federal shares are for each type of cost – that is, state personnel, non-personnel, or contractor – any other funding has to be deducted from those costs. However, other funding is applied to the entire activity, so it is necessary to determine how much of the other funding to deduct from each cost type.

The solution is calculate the proportion of each cost type, and then deduct the same proportion of other funding from that cost.

<details open>
<summary><b>Simplified Example:</b></summary>
Here is an activity for FFY 2023. Only the totals are shown.

|Cost                   |Action|Total    |
|-----------------------|------|---------|
| State personnel total |      | $2,000  |
| Non-personnel total   | +    | $3,000  |
| Contractor total      | +    | $5,000  |
| **Activity total**    | =    | $10,000 |
| Other funding         | -    | $2,000  |
| **Medicaid total**    |      | $8,000  |
| **Federal share**     | 90%  | $7,200  |
| **State share**       | 10%  | $800    |

|Proportion       |Math              |Value|
|-----------------|------------------|-----|
| State personnel | `$2,000/$10,000` | 20% |
| Non-personnel   | `$3,000/$10,000` | 30% |
| Contractor      | `$5,000/$10,000` | 50% |

|Cost             |Federal share math | Federal share |State share math | State share |
|-----------------|-------------------|---------------|-----------------|-------------|
| State personnel | `$7,200 × 20%`    | `$1,440`      | `$800 × 20%`    | `$160`      |
| Non-personnel   | `$7,200 × 30%`    | `$2,160`      | `$800 × 30%`    | `$240`      |
| Contractor      | `$7,200 × 50%`    | `$3,600`      | `$800 × 50%`    | `$400`      |
</details>

These per-cost federal and state shares are calculated for each activity, for each fiscal year. Furthermore, they are also calculated for each fiscal quarter by using the activity quarterly federal distribution. (In that calculation, state personnel and non-personnel costs are combined into a single "in-house" cost category.)

Activity grand totals, summed across all fiscal years, are also computed:

- **Activity grand total** - the sum of all fiscal year activity total costs
- **Activity Medicaid grand total** - the sum of all fiscal year activity Medicaid total costs
- **Activity federal grand total** - the sum of all fiscal year federal shares
- **Activity state grand total** - the sum of all fiscal year state shares

|                               | Math                      | Value        |
|-------------------------------|---------------------------|--------------|
| Activity grand total          | `$1,230,500 + $1,149,000` | `$2,379,500` |
| Activity Medicaid grand total | `$1,225,500 + $1,149,000` | `$2,374,500` |
| Activity federal grand total  | `$1,102,950 + $861,750`   | `$1,964,700` |
| Activity state grand total    | `  $122,550 + $287,250`   | `  $409,800` |

### Program costs

The budget tables need to account for the costs attributable to each match rate. First, the Key State Personnel totals are added for each federal fiscal year. Then the total, Medicaid, federal, and state shares of each cost category (state personnel, non-personnel, or contractor) are calculated for each activity of each match rate for each federal fiscal year. That is, if an activity is an 90/10 DDI activity, its costs will *only* contribute to the 90/10 DDI costs. The three cost categories are also summed together for each fiscal year to create a combined cost to the program for the fiscal year. Finally, the fiscal year costs are summed together to create a grand total cost to the program.
</details>
