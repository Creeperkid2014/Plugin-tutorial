# Plugin-tutorial
Beginner Minecraft Plugin Developer Starter Guide
1. Learn Java (The Easy Way for MC Devs)
What You Need to Know:
Variables & Data Types

If-Else, Loops (for, while)

Classes and Methods

Listeners and Interfaces

How packages and imports work

Recommended Java Tutorial Playlist:
BroCode Java Tutorial (YouTube)
(3 hours, covers basics to OOP — perfect for plugin devs)

2. Setting Up Your First Plugin (Paper)
Tools You Need:
IntelliJ IDEA (Community)

Java 17 SDK (Adoptium)

Paper server jar (papermc.io)

Gradle (comes bundled with IntelliJ or install separately)

Folder Layout:
css
Copy
Edit
MyFirstPlugin/
├── src/
│   └── main/
│       └── java/
│           └── com/yourname/myplugin/
│               └── MyPlugin.java
├── plugin.yml
├── build.gradle
3. plugin.yml Example
yaml
Copy
Edit
name: MyFirstPlugin
version: 1.0
main: com.yourname.myplugin.MyPlugin
api-version: 1.20
commands:
  hello:
    description: Say hello!
4. Basic Events & Code Examples
1. Simple Command
java
Copy
Edit
@Override
public boolean onCommand(CommandSender sender, Command command, String label, String[] args) {
    if (command.getName().equalsIgnoreCase("hello")) {
        sender.sendMessage("Hello from your first plugin!");
        return true;
    }
    return false;
}
2. Player Movement Event
java
Copy
Edit
@EventHandler
public void onPlayerMove(PlayerMoveEvent event) {
    Player player = event.getPlayer();
    player.sendMessage("You moved!");
}
3. Player Join Message
java
Copy
Edit
@EventHandler
public void onJoin(PlayerJoinEvent event) {
    event.setJoinMessage("Welcome, " + event.getPlayer().getName() + "!");
}
4. Give Player an Item on Command
java
Copy
Edit
if (command.getName().equalsIgnoreCase("giveitem")) {
    if (sender instanceof Player player) {
        player.getInventory().addItem(new ItemStack(Material.DIAMOND));
        player.sendMessage("Enjoy your diamond!");
        return true;
    }
}
5. Recommended Video Tutorials
Kody Simpson - MC Plugin Dev (2023) – Short and clean tutorial

Appljuze - Bukkit Plugin Tutorials – Detailed commands & events

TheSourceCode - Full Plugin Tutorial – Builds a full plugin from scratch

6. Projects to Try First
/hello – a simple chat command

/feed – sets player’s food level to max

Join & Quit messages using PlayerJoinEvent and PlayerQuitEvent

Movement tracker: show player coordinates on move

/givewand – gives a magic stick item

7. Bonus Tips
Test your plugin on a local Paper server

Avoid overusing static — it can cause issues

Use getLogger().info("message") to debug in console

Use Gradle to automate compiling and building jars

Organize your source code with clear packages

