## APD Auto-Save

![sequence-diagram-auto-saving](https://user-images.githubusercontent.com/62778/221680538-f0b36619-1772-4e19-aa1a-de8829083e40.png)

Every APD change in the application is made via the Patch store and the Save Middleware service. Changes are converted into JSON patches and added to the Patch store queue. For most of the fields in the APD form, the changes are saved to the Patch store as they are being changed, using the onChange function in the field. For subforms (Key State Personnel, State Staff, State Expenses, Contractors, Milestones, Outcomes, and Metrics) and the new APD form the data submitted to the appropriate Redux Action when the user clicks the save button. Then the action creates the appropriate JSON patches and adds them to the queue.

JSON patches join the Patch store queue as changes are made throughout the system. Once every 300ms, the Save Middleware service triggers a save APD action that checks the queue, if there are changes in it, then save APD collects them and sends them to the API as an array of JSON patches. Those patches are applied to the APD. The APD is validated. The budget is updated, if any values related to it change. The changes are saved and then returned to the save APD action. It updates the APD and Budget Redux stores with any updates.

If a save is still running after 300ms, the next save is added to a queue and performed once the current one is finished running.