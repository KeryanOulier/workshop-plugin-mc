# WorkshopPluginMc

Workshop for Epitech Paris, about creating a minecraft plugin with spigot 1.19.3

## Pre-requisites

- Minecraft 1.19.3
- [Latest Java JDK](https://www.oracle.com/java/technologies/downloads/#jdk19-windows)
- [Spigot 1.19.3 from BuildTool](https://www.spigotmc.org/wiki/buildtools/)
- [Maven](https://maven.apache.org/)
- [Visual Studio Code](https://code.visualstudio.com/)
- vscode's [Java Extension Pack](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack)

## Step 1 - create a server

First, create a folder for your server with the "spigot-1.19.3.jar" file in it. Then create an executable file based on your OS (<https://www.spigotmc.org/wiki/spigot-installation/#installation>).

Then run it. It should create some file and print this:

```txt
You need to agree to the EULA in order to run the server. Go to eula.txt for more info.
```

Open the "eula.txt" file and change the "eula=false" to "eula=true". Then run the server again. It should now start and finish preparing the server.

The server is now ready to be used.

You can check the official minecraft documentation to better personalize the server.

### Useful server commands

- stop: stop the server
- restart: restart the server
- help: show all commands

## Step 2 - create a blank plugin

First we need to create a java project.
To do so we will use the [Java Extension Pack](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack) of vscode.

- Create a folder named plugin
- Right-click on it and select "Create Maven Project"
- Select "maven-archetype-quickstart"
- Choose the latest version
- Enter your GroupId (usualy it is com.YOUR_PSEUDO)
- Name your project
- Select the folder where you want to create your project (it should already have select the good one).

After that, the terminal will pop up and you will need to precise the version of the project (1.0-SNAPSHOT is the default value). Then press "enter" and the project should be created.

The modify the pom.xml and add this in the dependencies:

```xml
<repositories>
    <!-- This adds the Spigot Maven repository to the build -->
    <repository>
        <id>spigot-repo</id>
        <url>https://hub.spigotmc.org/nexus/content/repositories/snapshots/</url>
    </repository>
</repositories>

<dependencies>
    <!--This adds the Spigot API artifact to the build -->
    <dependency>
           <groupId>org.spigotmc</groupId>
           <artifactId>spigot-api</artifactId>
           <version>1.19.3-R0.1-SNAPSHOT</version>
           <scope>provided</scope>
    </dependency>
</dependencies>
```

Create a new file named "plugin.yml" in src/main/resources and add this in:

```yaml
main: com.example.App (the path from the src/main/java folder to the file App.java)
name: YOUR_PROJECT_NAME
version: 1.0-SNAPSHOT
```

Open "App.java" and add change it to this:

```java
package com.example;
import org.bukkit.plugin.java.JavaPlugin;

public class App extends JavaPlugin {

}
```

From the "maven" tab, click on your project and then on "Lifecycle" and then on "package". It should build a jar file in the "target" folder. Copy or move it in the "plugins" folder of the server. Then run the server and it should load your plugin. You can check the console to see if it is loaded or use the "plugins" command.

[Spigot documentation](https://hub.spigotmc.org/javadocs/spigot/index.html)

## Step 3 - hello world

Now that you have a plugin, add:

- An "onEnable" function in the App.java to print "Hello world" in the console.
- An "onDisable" function in the App.java to print "Goodbye world" in the console.

<!-- TODO -->
## Step 4 - events

Use an [event](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/package-summary.html) to send "Hello PLAYER_NAME !" to the player when the player join the server, where PLAYER_NAME is the name of the player that joined.

<!-- TODO -->
## Step 5 - commands

Create 2 [commands](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/command/package-summary.html):

- "/hello" that send "Hello world" to the player.
- "/my_say msg" that send "msg" to the player.

<!-- TODO -->
## Step 6 - items

Create 2 custom [items](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemStack.html):

- A "nether_start" named "Welcome" with a **lore** that say "Welcome to the world" given to the player when he joined.
- A "Gold_sword" named "Excalibur" enchanted with **sharpness 5** and the unbreakable keyword, that you can get by using a "/sword" command.
