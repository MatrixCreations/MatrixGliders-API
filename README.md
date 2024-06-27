# MatrixGliders-API
⚠️ This repository doesn't contain MatrixGliders source code. You'll still need real copy of MatrixGliders to use this API into your project. 

MatrixGliders is a Minecraft plugin that enhances gameplay by introducing customizable gliders for players. It features an intuitive GUI for managing and equipping gliders, seamless PlaceholderAPI integration for displaying player statistics, and robust permissions for command management. The plugin also supports custom model data, and integrates with ItemsAdder and Oraxen for even more customization options. Perfect for adding a new dimension of fun and functionality to your Minecraft server!

JavaDocs: https://itsharshxd.github.io/MatrixGliders-API/index.html \
Documentation: https://github.com/ItsHarshXD/MatrixGliders-API/wiki

![GitHub Release](https://img.shields.io/github/v/release/ItsHarshXD/MatrixGliders-API?display_name=release&label=API%20Version)

## Integrate MatrixGliders API
To use MatrixGliders in your project implement MatrixGliders dependency into your Maven/Gradle project.

## Maven Integration
1. Add this in your repository section.
```xml
<repository>
    <id>jitpack-repo</id>
    <url>https://jitpack.io</url>
</repository>
```

2. Add this in your dependency section

> [!CAUTION]
> Replace "**VERSION**" with latest release version given up.

```xml
<dependency>
  <groupId>org.itsharshxd</groupId>
  <artifactId>matrixgliders</artifactId>
  <version>VERSION</version>
</dependency>
```

## Gradle Integration
1. Add this in your repository section. (Gradle intergration is a bit messy! You need GitHub secret key to use this.)
```gradle
repositories {
    mavenCentral()
    repositories {
        maven {
            url = uri("https://maven.pkg.github.com/ItsHarshXD/MatrixGliders-Repo")
            credentials {
                username = project.findProperty("gpr.user") ?: System.getenv("USERNAME")
                password = project.findProperty("gpr.key") ?: System.getenv("TOKEN")
            }
        }
    }
}
```

2. Add this in your dependency section

> [!CAUTION]
> Replace "**VERSION**" with latest release version given up. (Don't include "v")

```gradle
dependencies {
    implementation 'org.itsharshxd:matrixgliders:VERSION'
}
```

## __API Overview__

### API Events
1. **PlayerGlideEvent** - Triggers when any player is in gliding state.

```java
@EventHandler
public void whilePlayerGlide(PlayerGlideEvent event) {
  List<Player> players = event.getPlayers();
  // Do something
}
```

2. **GlidingStartEvent** - Triggers when any player starts gliding.

```java
@EventHandler
public void glidingStartEvent(GlidingStartEvent event) {
  Player player = event.getPlayer();
  // Do something
}
```

3. **GlidingEndEvent** - Triggers when any player stops gliding.

```java
@EventHandler
public void glidingEndEvent(GlidingEndEvent event) {
  Player player = event.getPlayer();
  // Get the cause, which led the player to stop gliding! It can be either "LANDING" or "DISCONNECT".
  Cause cause = event.getCause();
  if(cause.equals(Cause.DISCONNECT)) {
    // Do something
  }
}
```

### API Methods:
```java
void startGlide(Player player) //Starts gliding for the specified player
void stopGlide(Player player, Cause cause) //Stops gliding for the specified player
boolean isGliding(Player player) //Checks if the player is currently gliding
void addGliderToPlayer(Player player, String gliderID) //Adds a glider to the specified player
void removeGliderFromPlayer(Player player, String gliderID) //Removes a glider from the specified player
boolean hasGliderEquipped(Player player) //Checks if the specified player has a glider equipped
void wearEquippedGlider(Player player) //Equips the glider for the specified player
void equipGliderToConfig(Player player, String gliderID) //Equips a glider to the config for the specified player
void disrobeEquippedGlider(Player player) //Disrobes the equipped glider for the specified player
void unequipGliderFromConfig(Player player) //Unequips a glider from the config for the specified player
boolean isValidGliderID(String gliderID) //Checks if the specified glider ID is valid
List<String> getTotalGliders() //Gets the list of all gliders
List<String> getPlayerGliders(Player player) //Gets the list of gliders for the specified player
```
