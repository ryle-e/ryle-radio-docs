*abstract*
**Inherits from** : MonoBehaviour

This is the main base class for components that refer to a [[RadioData]] in some way in order to function, e.g [[RadioBroadcaster]], [[RadioInsulator]]. It allows for a Data to appear automatically in the inspector and for all components to be globally initialized.

To set up a class to select tracks from the listed Data, we use [[RadioComponentTrackAccessor]].

## Usage
You can't create a RadioComponent on its own- it is just a base class for some other components.

## Custom Classes
