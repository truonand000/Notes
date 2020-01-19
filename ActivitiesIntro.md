# Android Activities Intro

# Table of Contents
  - [Concept Of Activities](#Concept-Of-Activities)
  - [Configuring the Maniest](#Configuring-The-Manifest)

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
          <activity android:name="*.ExampleActivity"/>
          ...
        </appliaciton ...>
      </manifest>

    ```
    - The only required attribute for this element is `android:name`
      - Specifies the class name of the activity.
    - Can add attributes that define activity characteristics:
      - Label
      - Icon
      - UI theme


### Declare intent filters

- `Intent filters` are a powerful feature of the Android Platform:
  - Ability to launch an activity based on `explicit request` and `implicit requests`.
    - Example:
      - explicit request might tell the system to "Start the Send Email actiity in the Gmail app"
      - implicit request might tell system to "Start a Send Email screen in any actiity that can do the job"
      ```python

        name = "What ?"
        nothing = 4

        def function s():
          for i in range(10):
            print(i)

      ```



