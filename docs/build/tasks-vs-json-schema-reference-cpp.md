---
title: Tasks. vs. JSON – Referenční dokumentace schématu (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: cc6b2983d3cc3d40449357a554df5feee38c21d9
ms.sourcegitcommit: 6c1960089b92d007fc28c32af1e4bef0f85fdf0c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556653"
---
# <a name="tasksvsjson-schema-reference-c"></a>Tasks. vs. JSON – Referenční dokumentace schématu (C++)

Chcete-li aplikaci Visual Studio sdělit, jak vytvořit zdrojový kód v projektu otevřené složky, přidejte soubor *Tasks. vs. JSON* . Můžete definovat libovolný libovolný úkol a potom ho vyvolat z místní nabídky **Průzkumník řešení** . Projekty CMake nepoužívají tento soubor, protože všechny příkazy sestavení jsou zadány v souboru *CMakeLists. txt*. Pro jiné systémy sestavení než CMake, *Tasks. vs. JSON* je místo, kde můžete zadat příkazy sestavení a vyvolat skripty sestavení. Obecné informace o použití *Tasks. vs. JSON*najdete v tématu [přizpůsobení úloh sestavování a ladění pro vývoj "otevření složky"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

`type` Úloha má vlastnost, která může mít jednu ze čtyř hodnot: `default`, `launch`, `remote`nebo. `msbuild` Většina úloh by měla `launch` být použita, pokud není vyžadováno vzdálené připojení.

## <a name="default-properties"></a>Výchozí vlastnosti

Výchozí vlastnosti jsou k dispozici pro všechny typy úloh:

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`taskLabel`|řetězec| (Povinné.) Určuje popisek úlohy použitý v uživatelském rozhraní.|
|`appliesTo`|řetězec| (Povinné.) Určuje, na kterých souborech lze příkaz provést. Je podporováno použití zástupných znaků, například: "*", "*. cpp", "/*. txt"|
|`contextType`|řetězec| Povolené hodnoty: "vlastní", "Build", "Vyčištění", "znovu sestavit". Určuje, kde se v místní nabídce zobrazí úkol. Výchozí hodnota je Custom (vlastní).|
|`output`|řetězec| Určuje výstupní značku k úkolu.|
|`inheritEnvironments`|pole| Určuje sadu proměnných prostředí děděných z více zdrojů. Můžete definovat proměnné v souborech, jako je *CMakeSettings. JSON* nebo *CppProperties. JSON* , a zpřístupnit je kontextu úlohy. **Visual Studio 16,4:**: určení proměnných prostředí v jednotlivých úlohách pomocí `env.VARIABLE_NAME` syntaxe. Chcete-li proměnnou zrušit, nastavte ji na hodnotu null.|
|`passEnvVars`|Boolean| Určuje, zda zahrnout do kontextu úlohy další proměnné prostředí. Tyto proměnné se liší od těch, které jsou definovány `envVars` pomocí vlastnosti. Výchozí hodnota je "true".|

## <a name="launch-properties"></a>Vlastnosti spuštění

Když je `launch`typ úkolu, jsou k dispozici tyto vlastnosti:

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`command`|řetězec| Určuje úplnou cestu procesu nebo skriptu, který se má spustit.|
|`args`|pole| Určuje čárkami oddělený seznam argumentů předaných příkazu.|
|`launchOption`|řetězec| Povolené hodnoty: "none", "ContinueOnError", "IgnoreError". Určuje, jak pokračovat v příkazu, když dojde k chybám.|
|`workingDirectory`|řetězec| Určuje adresář, ve kterém se příkaz spustí. Použije se výchozí hodnota aktuálního pracovního adresáře projektu.|
|`customLaunchCommand`|řetězec| Určuje globální přizpůsobení oboru, které se má použít před provedením příkazu. Užitečné pro nastavení proměnných prostředí, jako je% PATH%.|
|`customLaunchCommandArgs`|řetězec| Určuje argumenty pro customLaunchCommand. (Vyžaduje `customLaunchCommand`.)|
 `env`| Určuje seznam klíčových hodnot vlastních proměnných prostředí. Například "myEnv": "myVal"|
|`commands`|pole| Určuje seznam příkazů, které se mají vyvolat v daném pořadí.|

### <a name="example"></a>Příklad

Následující úlohy vyvolávají příkaz *make. exe* , když je soubor pravidel zadán ve složce a `Mingw64` prostředí bylo definováno v souboru *CppProperties. JSON*, jak je znázorněno v [odkazu schématu CppProperties. JSON](cppproperties-schema-reference.md#user_defined_environments):

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

Tyto úlohy lze vyvolat z kontextové nabídky po kliknutí pravým tlačítkem na soubor *. cpp* v **Průzkumník řešení**.

## <a name="remote-properties"></a>Vzdálené vlastnosti

Vzdálené úlohy jsou povolené při instalaci nástroje pro vývoj pro Linux pomocí C++ a přidání připojení ke vzdálenému počítači pomocí Správce připojení sady Visual Studio. Vzdálená úloha spouští příkazy ve vzdáleném systému a může do ní také kopírovat soubory.

Když je `remote`typ úkolu, jsou k dispozici tyto vlastnosti:

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`remoteMachineName`|řetězec|Název vzdáleného počítače. Musí odpovídat názvu počítače ve **Správci připojení**.|
|`command`|řetězec|Příkaz, který se má odeslat do vzdáleného počítače. Ve výchozím nastavení jsou příkazy spouštěny v $HOME adresáři na vzdáleném systému.|
|`remoteWorkingDirectory`|řetězec|Aktuální pracovní adresář na vzdáleném počítači.|
|`localCopyDirectory`|řetězec|Místní adresář, který se má zkopírovat do vzdáleného počítače. Výchozí hodnota je aktuální pracovní adresář.|
|`remoteCopyDirectory`|řetězec|Adresář ve vzdáleném počítači, do kterého `localCopyDirectory` se kopíruje.|
|`remoteCopyMethod`|řetězec| Metoda, která se má použít pro kopírování Povolené hodnoty: "none", "SFTP", "rsync". rsync se doporučuje pro velké projekty.|
|`remoteCopySourcesOutputVerbosity`|řetězec| Povolené hodnoty: "normální", "Verbose", "Diagnostic".|
|`rsyncCommandArgs`|řetězec|Výchozí hodnota je-t--DELETE.|
|`remoteCopyExclusionList`|pole|Čárkami oddělený seznam souborů v `localCopyDirectory` pro vyloučení z operací kopírování.|

### <a name="example"></a>Příklad

Následující úloha se zobrazí v místní nabídce, když kliknete pravým tlačítkem myši na *Main. cpp* v **Průzkumník řešení**. Závisí na vzdáleném počítači, který `ubuntu` se nazývá **Správce připojení**. Úloha zkopíruje aktuální otevřenou složku v aplikaci Visual Studio do `sample` adresáře na vzdáleném počítači a potom vyvolá g + +, aby program sestavil.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>vlastnosti nástroje MSBuild

Když je `msbuild`typ úkolu, jsou k dispozici tyto vlastnosti:

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`verbosity`|řetězec| Určuje verbosityAllowed hodnoty výstupu sestavení projektu nástroje MSBuild: "quiet", "minimální", "Normal", "detailed", "Diagnostics".|
|`toolsVersion`|řetězec| Určuje verzi sady nástrojů pro sestavení projektu, například "2,0", "3,5", "4,0", "Current". Výchozí hodnota je Current (aktuální).|
|`globalProperties`|objekt|Určuje seznam klíčových hodnot globálních vlastností, které mají být předány do projektu, například "konfigurace": "Release"|
|`properties`|objekt| Určuje seznam klíč-hodnota dalších vlastností pouze projektu.|
|`targets`|pole| Určuje seznam cílů, které mají být vyvolány, v pořadí v projektu. Výchozí cíl projektu se používá, pokud nejsou zadány žádné.|
