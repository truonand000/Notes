# Android Activities Intro

## Concept Of Activities

- Most apps contain multiple screens, meaning they have mutiple activities
  - One activity in an app is sprecified as the main activity
  - Each activity can start another activity in order to perform different actions

- Activities are only loosely bound to the other activities.
  - Minimal dependendencies among the activities in an app.
  - Activities often start up activities belonging to other apps.

- To use activities in app:
  - Register info about them in app's manifest.
  - Manage activity lifeycles appropriately


## Configuring The Manifest

- For app to be able to use activities:
  - Must declare the activities in manifest
    - Declare certain attributes

  ### Declare Activities
  - To declare activity:
    - Open maifest file and add an `<activity>` element as a child of the `<application>` element.
    - For example:
      ```xml

      <manifest ...>
        <application ...>
          <activity android:name=" .ExampleActivity"/>
          ...
        </appliaciton ...>
      </manifest>

      ```



