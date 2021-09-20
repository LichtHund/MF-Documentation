# Adventure

{% hint style="info" %}
I recommend using adventure over the bukkit version of this lib.
{% endhint %}

MF-MSG now supports [**Kyori's Adventure**](https://github.com/KyoriPowered/adventure). Which allows you to use the lib on many other platforms and has all the benefits of using Adventure.

{% tabs %}
{% tab title="Gradle" %}
You need to add the dependency to your `build.gradle`.

```groovy
repositories {
    maven { url = 'https://repo.mattstudios.me/artifactory/public' }
}

dependencies {
    implementation "me.mattstudios:triumph-msg-adventure:{version}" // Replace version here 
}
```

In order to include the lib in your project, you need to add `shadowJar` plugin `build.gradle`.  
Replace `[YOUR PACKAGE]`with your plugin's package, for example `me.myplugin.plugin`.

```groovy
apply plugin: 'com.github.johnrengelman.shadow'

shadowJar {
   relocate 'me.mattstudios.msg', '[YOUR PACKAGE].mfmsg'
}
```
{% endtab %}

{% tab title="Maven" %}
You need to add the dependency to your `pom.xml`.

```markup
<dependency>
  <groupId>me.mattstudios</groupId>
  <artifactId>triumph-msg-adventure</artifactId>
  <version>{version}</version> <!-- replace version here -->
</dependency>
```

In order to include the framework in your project, you need to add the following to your `pom.xml`, in the plugins section.  
Replace `[YOUR PACKAGE]`with your plugin's package, for example `me.myplugin.plugin`.

```markup
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-shade-plugin</artifactId>
    <version>3.1.1</version>
    <configuration>
        <relocations>
            <relocation>
                <pattern>me.mattstudios.msg</pattern>
                <shadedPattern>[YOUR PACKAGE].mfmsg</shadedPattern> <!-- Replace package here here -->
            </relocation>
        </relocations>
    </configuration>
    <executions>
        <execution>
            <phase>package</phase>
            <goals>
                <goal>shade</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```
{% endtab %}
{% endtabs %}

### Using it

There are some major diferences between the bukkit version and this version of the lib.
For starters, you use `AdventureMessage` instead of `BukkitMessage`.
The lib also just parses the text to an Adventure component. You will have to use Adventure to make it into a BossBar, Title or SubTitle. You will also have to use Adventure's audiences to deliver the messages.

```java
final AdventureMessage message = AdventureMessage.create();
```



