This page exists as a guide to help the developer target what changes need to be made with a database model update.

## When making a change to a model schema:
- [ ] [Update the relevant model schemas](#update-model-schemas)
- [ ] [Update the relevant seed files](#seed-files) (seeds exist under both `seeds/development` and `seeds/testing` directories)
- [ ] [Update the relevant api files](#api-files)
- [ ] [Update existing APDs in the database via a migration script](#migrations)
- [ ] Update the joi schemas in the common directory
- [ ] Front end changes (such as patches for redux)

### Model Schemas
In `models/apd.js`, `apdSchema` is the base model for an APD.
It may contain other nested schemas, such as:
- `activitySchema` found in `models/apdActivity.js` as the base activity model
- `budgetSchema` found in `models/budget.js` as the base budget model

Because this project sets up APD of different types (HITECH, MMIS), there are also schemas for the types that expand (by inheritance) on the base schemas. That also means you can overwrite fields (if necessary) that exist in the base schema by whatever schema is inheriting the base.

Example (not an exhaustive list): 
| Base schema | Schema that inherits base schema | APD Type |
|-|-|-|
| `apdSchema` | `hitechSchema` | HITECH |
| `apdSchema` | `mmisSchema` | MMIS |
| `activitySchema` | `hitechActivitySchema` | HITECH |
| `activitySchema` | `mmisActivitySchema` | MMIS |
| `budgetSchema` | `hitechBudgetSchema` | HITECH |
| `budgetSchema` | `mmisBudgetSchema` | MMIS |

### Seed Files
Seed files exist in both `seeds/development` and `seeds/testing` directories

### API Files
Relevant updates could include files for when a new APD is created (`post.data.js` which is the APD-type-shared structure, and possibly the file that contains APD-type-specific structure, like `post.mmis.data.js`)

### Migrations

#### Create a migration file
1. Create a scaffolding migration file
From the api directory, run: (_file name should describe update and should have “mongoose” prefix for Mongo-related changes)_
```
yarn run make-migrate mongoose-example-file
```
2. Modify the migration file - this code will update existing data in the database to conform to your model changes
3. Use the `up` method to change the current database items to match your new model
4. Use the `down` method to change the database items back to how they were before the migration ran

_Note:_ When doing a replace for budgets, make sure to include the discriminator, `__t`, to indicate the budget type on the generic Budget model.
e.g.
```
Budget.replaceOne(
  { ...budget, __t: BUDGET_TYPE.MMIS_BUDGET },
  ...
)
```

#### Test the migration file
Test this by running the migration. The command must be run inside the container: so you should either attach to the container and run it as
```
yarn migrate
```
or to run it from your local terminal run
```
docker compose exec api yarn migrate
```
Test this multiple times on the same data to ensure this has consistent results. You can delete the migration file from postgres locally, rerun the seed to reset the data, then add the migration file back and repeat.

#### Run the migration file
From the api directory, run as explained above.


