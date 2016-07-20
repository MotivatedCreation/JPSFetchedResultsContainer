# JPSFetchedResultsContainer
A NSFetchedResulterController container that can be used to fetch multiple entity types. With this container, you can still take advantage of the benefits that each individual NSFetchedResultsController offers such as, section, caching, etc.

# Usage

### Allocating a Container
`let fetchedResultsContainer = JPSFetchedResultsContainer(fetchedResultsControllers: [...], managedObjectContext: context)`<br />
`fetchedResultsController.delegate = self;`

**OR**

`let fetchedResultsContainer = JPSFetchedResultsContainer(fetchRequests: [...], managedObjectContext: context)`<br />
`fetchedResultsController.delegate = self;`

### Delegate
`func containerWillChangeContent(container: JPSFetchedResultsContainer)`

`func containerDidChangeContent(container: JPSFetchedResultsContainer)`

`func container(container: JPSFetchedResultsContainer, didChangeSection sectionInfo: NSFetchedResultsSectionInfo, atIndex sectionIndex: Int, forChangeType type: NSFetchedResultsChangeType)`

`func container(container: JPSFetchedResultsContainer, didChangeObject anObject: AnyObject, atIndexPath indexPath: NSIndexPath?, forChangeType type: NSFetchedResultsChangeType, newIndexPath: NSIndexPath?)`

### Empty Sections
`NSFetchedResultsController.empty()`

### Fetching
`fetchedResultsContainer.performFetch()`

### Obtaining objects
`let indexPath = NSIndexPath(...)` <br />
`fetchedResultsContainer.objectAtIndexPath(indexPath)`

`let managedObject = ...` <br />
`fetchedResultsContainer.indexPathForObject(managedObject)`

### Obtaining Number of Objects per Section
`let section = 0` <br />
`fetchedResultsContainer.numberOfObjectsInSection(section)`

### Changing FetchedResultsControllers

`let index = 0` <br />
`let withFetchedResultsController = ...` <br />
`fetchedResultsContainer.replaceFetchedResultsControllerAtIndex(index, withFetchedResultsController: withFetchedResultsController)`

**OR**

`let aFetchedResultsController = ...` <br />
`let withFetchedResultsController = ...` <br />
`fetchedResultsContainer.replaceFetchedResultsControllerAtIndex(aFetchedResultsController, withFetchedResultsController: withFetchedResultsController)`
