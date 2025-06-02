The APD budget calculations are a little complicated, mostly because of the repetition. This document will walk through all the numbers that are calculated, where they come from, and where they show up in the eAPD.

<details open>
<summary><h2>User inputs</h2></summary>

All of the calculations begin with user inputs.


### APD Key Personnel

The first budget-related user input is related to APD Key Personnel. If key personnel have costs that are directly attributable to the program addressed by the APD, their costs are entered for each federal fiscal year covered by the APD.

**Example:** For an APD that covers FFY 2020 and 2021, the state has identified three key personnel. Only two of them have costs that are directly attributable to the APD.

|Key Personnel|Has costs|FFY 2020 costs|FFY 2021 costs|
|-------------|:-------:|--------------|--------------|
| Amber       | Yes     | $24,000      | $32,000      |
| Bob         | Yes     | $19,000      | $22,000      |
| Caitlin     | No      |              |              |

Key personnel are the only APD-level user-input that is incorporated into the APD budget. All other user-inputs are inside activities. For HITECH APDs, the key personnel are added to the Program Administration activity.


### Activity program type

Each activity is assigned a Medicaid program type. The options are HIT, HIE, and MMIS. The program type is used to determine program costs later.


### Activity state staff costs

Each activity can contain a list of state personnel who will be working on that activity. These state staff are not individuals but rather roles (e.g., "project assistant"). For each state staff role, the role's ***total*** costs, including benefits, are entered for each fiscal year. Then, their FTEs attributable to the activity are also entered for each fiscal year. Finally, their cost attributable to the activity is calculated by multiplying the total cost by the FTEs.

**Example:** For an APD covering FFY 2020 and 2021, the state has identified two state personnel.

|Personnel title    |Total Costs|FTE  |Activity Cost|
|-------------------|-----------|-----|-------------|
| Project assistant |           |     |             |
| --- FFY 2020      | $95,000   | 0.7 | $66,500*    |
| --- FFY 2021      | $98,500   | 1   | $98,500*    |
| Accountant II     |           |     |             |
| --- FFY 2020      | $112,000  | 2   | $224,000*   |
| --- FFY 2021      | $114,500  | 3   | $343,500*   |

\* indicates a calculated value


### Activity state non-personnel costs

Each activity can include a list of non-personnel costs for things like equipment and supplies purchases, travel costs, or training and outreach. These costs are entered for each federal fiscal year covered by the APD.

**Example:** For an APD covering FFY 2020 and 2021, the state has identified three non-personnel costs.

|Cost category|FFY 2020 Cost|FFY 2021 Cost|
|-------------|-------------|-------------|
| Training    | $40,000     | $30,000     |
| Travel      | $22,000     | $19,000     |
| Misc        | $5,000      | $6,000      |


### Activity contractor resource costs

Each activity can include a list of private contractor resources. Each contractor will either have a fixed cost per federal fiscal year, or will be an hourly resource. In either case, the costs will be entered. For hourly resources, the total cost per federal fiscal year will be calculated.

**Example:** For an APD covering FFY 2020 and 2021, the state has identified two contractor resource costs.

|Contractor   |Hourly?|Hourly rate|Hours  |FFY Cost   |
|-------------|:-----:|-----------|-------|-----------|
| ACME        | No    |           |       |           |
| -- FFY 2020 |       |           |       | $230,000  |
| -- FFY 2021 |       |           |       | $180,000  |
| LexCorp     | Yes   |           |       |           |
| -- FFY 2020 |       | $300      | 2,000 | $600,000* |
| -- FFY 2021 |       | $310      | 1,000 | $310,000* |

\* indicates a calculated value


### Other funding

Each activity can be supported by other funding sources. Those must be reported as they affect how much of the total activity cost is to be borne by Medicaid. These other funding amounts are entered for each federal fiscal year covered by the APD.

**Example:** For an APD covering FFY 2020 and 2021, the state provides the following other funding amounts:

|FFY 2020|FFY 2021|
|--------|--------|
| $5,000 | $0     |


### Activity federal/state split

Activity costs are divided between federal and state for each federal fiscal year. This can be 90% federal/10% state, 75% federal/25% state, or 50% federal/50% state, depending on the type of work being performed in the activity for the fiscal year.

**Example:** For an APD covering FFY 2020 and 2021, the state identifies the following funding splits:

|         |FFY 2020|FFY 2021|
|---------|--------|--------|
| Federal | 90%    | 75%    |
| State   | 10%    | 25%    |


### Activity quarterly federal distribution

The federal share of an activity can be distributed to the state at different amounts over the course of the federal fiscal year. For example, if a state has a contract that will be signed in the second quarter, the state may request all of the federal share related to contracts to be paid in the second quarter rather than spread evenly across the fiscal year.

**Example:** For an APD covering FFY 2020 and 2021, the state requests federal funding at the following quarterly rates:

| |FFY 2020 Q1|FFY 2020 Q2|FFY 2020 Q3|FFY 2020 Q4|FFY 2021 Q1|FFY 2021 Q2|FFY 2021 Q3|FFY 2021 Q4|
|------------------|-----|------|-----|-----|-----|-----|-----|-----|
| In-house costs   | 25% | 25%  | 25% | 25% | 30% | 40% | 20% | 10% |  
| Contractor costs | 0%  | 100% | 0%  | 0%  | 50% | 50% | 0%  | 0%  |


### Summary of user inputs

- **APD Key Personnel** - one input per personnel with costs per federal fiscal year
- **Activity** - one set of all following inputs per activity
  - **State personnel** - two inputs per role with costs per federal fiscal year
  - **Non-personnel costs** - one input per cost with costs per federal fiscal year
  - **Contractor resources** - two or three inputs per resource with costs per federal fiscal year
  - **Federal/state split** - one input per federal fiscal year
  - **Quarterly distribution** - four inputs per federal fiscal year

</details>

<details open>
<summary><h2>Calculated values</h2></summary>

There are a lot of values that get calculated, and some of them are a little bit complicated. The first set of calculated values are intermediary – necessary for later calculations, but not the final numbers presented anywhere.


### Intermediary values

- **Activity state personnel cost per fiscal year** - calculated from the state personnel ***total*** cost and FTEs. This value is displayed live while the user is entering total cost and FTE values.
**Example:** This example is based on the Program Administration activity in a HITECH APD, so it also includes the Key personnel values.

|State Personnel    |FFY 2020      |FFY 2021      |Total         |
|-------------------|--------------|--------------|--------------|
| Amber             | `   $24,000` | `   $32,000` | `   $56,000` |
| Bob               | `+  $19,000` | `+  $22,000` | `+  $41,000` |
| Project assistant | `+  $66,500` | `+  $98,500` | `+ $165,000` |
| Accountant II     | `+ $224,000` | `+ $343,500` | `+ $567,500` |
| **Total**         | `= $333,500` | `= $604,000` | `= $829,500` |

- **Activity state non-personnel cost per fiscal year** - calculated from the state non-personnel ***total*** cost. This value is displayed live while the user is entering total cost.

**Example:**

|Non-personnel |FFY 2020     |FFY 2021     |Total         |
|--------------|-------------|-------------|--------------|
| Training     | `  $40,000` | `  $30,000` | `   $70,000` |
| Travel       | `+ $22,000` | `+ $19,000` | `+  $42,000` |
| Misc         | `+  $5,000` | `+  $6,000` | `+  $11,000` |
| **Total**    | `= $67,000` | `= $55,000` | `= $123,000` |

- **Activity contractor costs per fiscal year** - for contractor resources that are hourly, calculated from the hourly rate and the number of hours. This is displayed live while the user is entering the hourly rate and number of hours.

**Example:**

| Contractor |FFY 2020      | FFY 2021     | Total         |
|------------|--------------|--------------|---------------|
| ACME       | `  $230,000` | `  $180,000` | `   $410,000` |
| LexCorp    | `+ $600,000` | `+ $310,000` | `+  $910,000` |
| **Total**  | `= $830,000` | `= $490,000` | `= $1320,000` |

### Activity costs

- **Activity total cost per fiscal year** - the sum of all activity [state personnel](#activity-state-staff-costs), [non-personnel](#activity-state-non-personnel-costs), and [contractor resource](#activity-contractor-resource-costs) costs for the fiscal year

  | FFY  | Math                            | Activity total |
  |------|---------------------------------|----------------|
  | 2020 | `$333,500 + $67,000 + $830,000` | `$1,230,500`   |
  | 2021 | `$604,000 + $55,000 + $490,000` | `$1,149,000`   |

- **Activity Medicaid total cost per fiscal year** - the activity total cost minus any [other funding](#other-funding) amount for the fiscal year

  | FFY  | Math                  | Activity Medicaid total |
  |------|-----------------------|-------------------------|
  | 2020 | `$1,230,500 + $5,000` | `$1,225,500`            |
  | 2021 | `$1,149,000 - 0`      | `$1,149,000`            |

- **Activity federal share per fiscal year** - the Medicaid total multiplied by the federal share percentage from the [federal/state split](#activity-federalstate-split) for the fiscal year

  | FFY  | Math               | Activity federal share |
  |------|--------------------|------------------------|
  | 2020 | `$1,225,500 * 90%` | `$1,102,950`           |
  | 2021 | `$1,149,000 * 75%` | `$861,750`             | 

- **Activity state share per fiscal year** - the Medicaid total multiplied by the state share percentage from the [federal/state split](#activity-federalstate-split) for the fiscal year

  | FFY  | Math               | Activity state share |
  |------|--------------------|----------------------|
  | 2020 | `$1,225,500 * 10%` | `$122,550`           |
  | 2021 | `$1,149,000 * 25%` | `$287,250`           |

There are some additional intermediary values that are necessary for future calculations and are based on activity-per-fiscal year values, so those are calculated here:

- **State personnel proportion** - this is the proportion of the **activity total cost** for the fiscal year that is made up by state personnel costs.

  | FFY  | Math                         | State personnel proportion |
  |------|------------------------------|----------------------------|
  | 2020 | `$333,500/$1,230,500 = 0.27` | 27%                        |
  | 2021 | `$604,000/$1,149,000 = 0.52` | 52%                        | 

- **Non-personnel proportion** - this is the proportion of the **activity total cost** for the fiscal year that is made up by non-personnel costs.

  | FFY  | Math                        | Non-personnel proportion |
  |------|-----------------------------|--------------------------|
  | 2020 | `$67,000/$1,230,500 = 0.05` | 5%                       |
  | 2021 | `$55,000/$1,149,000 = 0.05` | 5%                       |

- **Contractor resources proportion** - this is the proportion of the **activity total cost** for the fiscal year that is made up by contractor resources costs.

  | FFY  | Math                         | Contractor resources proportion |
  |------|------------------------------|---------------------------------|
  | 2020 | `$830,000/$1,230,500 = 0.68` | 68%                             |
  | 2021 | `$490,000/$1,149,000 = 0.43` | 43%                             |



**Example:**
|FFY 2020         |Federal share                      | State share                    |
|-----------------|-----------------------------------|--------------------------------|
| State personnel | `$1,102,950 × 27% = ` $297,796.50 | `$122,550 × 27% = ` $33,088.50 |
| Non-personnel   | `$1,102,950 ×  5% = ` $55,147.50  | `$122,550 ×  5% = ` $6,127.50  |
| Contractor      | `$1,102,950 × 68% = ` $750,006    | `$122,550 × 68% = ` $83,334    |


|FFY 2021         |Federal share math               |State share                      |
|-----------------|---------------------------------|---------------------------------|
| State personnel | `$861,750 × 52% = ` $448,110    | `$287,250 × 52% = ` $149,370    |
| Non-personnel   | `$861,750 ×  5% = ` $43,087.50  | `$287,250 ×  5% = ` $14,362.50  |
| Contractor      | `$861,750 × 43% = ` $370,552.50 | `$287,250 × 43% = ` $123,517.50 |


What are those numbers for? They seem a little out of the blue. In order to understand how much the state and federal shares are for each type of cost – that is, state personnel, non-personnel, or contractor – any other funding has to be deducted from those costs. However, other funding is applied to the entire activity, so it is necessary to determine how much of the other funding to deduct from each cost type.

The solution is calculate the proportion of each cost type, and then deduct the same proportion of other funding from that cost.

<details open>
<summary><b>Simplified Example:</b></summary>
Here is an activity for FFY 2020. Only the totals are shown.

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

The budget tables need to account for the costs attributable to each program type (HIT, HIE, and MMIS). First, the total, Medicaid, federal, and state shares of each cost category (state personnel, non-personnel, or contractor) are calculated for each activity of each program type for each federal fiscal year. That is, if an activity is an HIE activity, its costs will *only* contribute to the HIE costs. The three cost categories are also summed together for each fiscal year to create a combined cost to the program for the fiscal year. Finally, the fiscal year costs are summed together to create a grand total cost to the program.

MMIS activities also must capture the total, Medicaid, federal, and state costs based on MMIS FFP level (90/10, 75/25, or 50/50). The same logic as above is applied, but further filtered based on federal/state split.

Finally, program costs for in-house (state personnel and non-personnel) and contractor costs are computed per federal fiscal quarter. This is done by summing up the federal costs calculated above, described under the "state personnel proportion" subsection.
</details>

See also: [Math flows mural that maps calculations to parts of the budget object](https://app.mural.co/t/ccs9461/m/eapd5455/1588711183141/acecb4562692e2b1e5bd412411b4d5c540d07b3e?sender=u36b310d91a67c9dfdcc39641)