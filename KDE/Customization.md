# Customization

## Latte dock

Latte dock can be made to look like mack toolbar

## Fonts on Application Launcher

On lower resolution devices like laptops the fonts for application launcher can appear to large.
There is no graphical configuration for this so configuration files need to be modified. The configuration for application launcher this is kept in a qml file.

```bash
/usr/share/plasma/plasmoids/org.kde.plasma.kicker/contents/ui/DashboardRepresentation.qml
```

This is the configuration that I modified.  
First is the search box

```js
TextEdit {
            id: searchHeading

            anchors {
                horizontalCenter: parent.horizontalCenter
            }

            y: (middleRow.anchors.topMargin / 2) - (smallScreen ? (height/10) : 0)

            font.pointSize: dummyHeading.font.pointSize * 0.7
            ...
        }
```

Then is the application categories column.

Favorites header

Main Grid header

Remember to make a copy of this configuration file as plasma upgrade will overwrite this file.
