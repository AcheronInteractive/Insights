# Insights (Acheron Interactive Fork)
**Note: Please don't create PRs to this unless you understand how patches work.**

### Fork features:
- Multi-version support (1.21.4 -> 1.21.10)
- Uses Mojang mappings to avoid Paper's plugin remapping
- Fixed error from the plugin mishandling air in scan messages.
- Dropped unnecessary shaded libraries
  - Smaller file size

<hr>

Insights is a plugin which scans arbitrary regions and applies block limitations on them. 
Insights' limits are super configurable, allowing for group limits, individual (permission-based) limits, and tile limits.
Each limit is able to be bypassed through permissions, which you can customize in the limits configuration.

Apart from all placeable materials, Insights also supports the limitation of the following static entities:
* Item Frames
* Glow Item Frames
* Armor Stands
* Paintings
* End Crystals

Insights applies a mapreduce design pattern to perform scans asynchronously,
thus keeping the main thread free from counting materials.
Insights also provides an extensive developer API to create your own custom defined region addons,
or to perform arbitrary scans and process those.

For a full description of this plugin, please refer to SpigotMC: https://www.spigotmc.org/resources/56489/

<div align="center" style="margin-top: 16px;">
  <a href="https://bstats.org/plugin/bukkit/Insights/7272">
    <img alt="bStats" src="https://bstats.org/signatures/bukkit/Insights.svg">
  </a>
</div>

## Extensions
These plugins are extensions on Insights, they must be placed in your `plugins/` folder.
* [InsightsWorldEditExtension](https://github.com/InsightsPlugin/InsightsWorldEditExtension) - Block materials through WorldEdit modifications.
  Supports Insights' limits & disallows any placement of limited blocks.

## Addons
Addons define regions for Insights to limit blocks in.
Instead of a limit per chunk, when a block is placed in such a region, it will first count all blocks in that region, and after enforce limits in that region.
Regions are cached to not bother with scans each time a block has been placed.
* [BentoBoxWorldAddon](https://github.com/InsightsPlugin/BentoBoxAddon/releases) - Limit blocks in your BentoBox world (includes bSkyBlock & AcidIslands)
* [GriefPreventionAddon](https://github.com/InsightsPlugin/GriefPreventionAddon/releases) - Limit blocks in your GriefPrevention claims!
* [USkyBlockAddon](https://github.com/InsightsPlugin/USkyBlockAddon/releases) - Limit blocks in your USB islands!
* [IridiumSkyblockAddon](https://github.com/InsightsPlugin/IridiumSkyblockAddon/releases) - Limit blocks in your Iridium islands!
* [PlotSquaredAddon](https://github.com/InsightsPlugin/PlotSquaredAddon/releases) - Limit blocks in your PlotSquared plots!
* [SuperiorSkyblock2Addon](https://github.com/InsightsPlugin/SuperiorSkyblock2Addon/releases) - Limit blocks in your SS islands!
* [LandsAddon](https://github.com/InsightsPlugin/LandsAddon/releases) - Limit blocks in your lands!
* [TownyAddon](https://github.com/InsightsPlugin/TownyAddon/releases) - Limit blocks in your towns!
* [GriefDefenderAddon](https://github.com/galexrt/InsightsGriefDefenderAddon/releases) by [galexrt](https://github.com/galexrt) - Limit your GriefDefender claims! 

## Compiling Acheron Interactive's fork of Insights
1. Run `git submodule update --init --recursive` in the repository's base directory to ensure the gitmodule is populated
2. Run `./patcher p` in the repository's base directory to patch the gitmodule with our patches
3. Run `./patcher b` in the repository's base diectory to build the patched version of Insights
4. Obtain the compiled jar from insight `Insights-Patched/jars/`

## Developer API
### Repository / Dependency
If you wish to use snapshot version of Insights, you can use the following repo:
```
https://repo.fvdh.dev/snapshots
```

#### Gradle:
```kotlin
repositories {
  compileOnly("dev.frankheijden.insights:Insights:VERSION")
}

dependencies {
  maven("https://repo.fvdh.dev/releases")
}
```

#### Maven:
```xml
<project>
  <repositories>
    <!-- Insights repo -->
    <repository>
      <id>fvdh</id>
      <url>https://repo.fvdh.dev/releases</url>
    </repository>
  </repositories>
  
  <dependencies>
    <!-- Insights dependency -->
    <dependency>
      <groupId>dev.frankheijden.insights</groupId>
      <artifactId>Insights</artifactId>
      <version>VERSION</version>
      <scope>provided</scope>
    </dependency>
  </dependencies>
</project>
```

### Addons
See the [Insights Wiki](https://github.com/InsightsPlugin/Insights/wiki/Addon-API) on how to implement your own addon for Insights!

## Screenshots
### Limit blocks per group
![GroupLimit](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/GroupLimit.png)
### Custom block limit per chunk
![CustomLimit](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/CustomLimit.png)
### Scan all blocks in a radius around you!
![ScanRadius](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/ScanRadius.png)
### Apply limitations to WorldEdit!
![WorldEditLimit](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/WorldEditLimit.png)
### Limit globally all tiles per chunk!
![TileLimit](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/TileLimit.png)
### Scan all tiles in chunks
![TileScan](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/TileScan.png)
### Scan with custom queries
![CustomScan](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/CustomScan.png)
### Automatically scan upon chunk entering
![AutoScan](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/AutoScan.png)
### Disable blocks in WorldGuard regions (Regex region match)
![RegionDisallow](https://raw.githubusercontent.com/InsightsPlugin/Insights/refs/heads/main/screenshots/RegionDisallow.png)
