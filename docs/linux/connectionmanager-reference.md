---
title: ConnectionManager – referenční dokumentace
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 1c6236cedba88714e9918dd2c096b5e78d2f08ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "77258030"
---
# <a name="connectionmanager-reference"></a>ConnectionManager – referenční dokumentace

::: moniker range="<=vs-2017"

ConnectionManager.exe je k dispozici ve Visual Studiu 2019 verze 16.5 a novější.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager.exe je nástroj příkazového řádku pro správu vzdálených vývojových připojení mimo aplikaci Visual Studio. Je to užitečné pro úkoly, jako je zřizování nového vývojového počítače. Nebo ji použijte k nastavení sady Visual Studio pro průběžnou integraci.Můžete ji použít v okně příkazového řádku pro vývojáře. Další informace o příkazovém řádku pro vývojáře naleznete [v tématu Použití sady nástrojů Microsoft C++ z příkazového řádku](../build/building-on-the-command-line.md).

ConnectionManager.exe je k dispozici ve Visual Studiu 2019 verze 16.5 a novější. Je součástí vývoje Linuxu s úlohami **C++** v Instalační službě Visual Studia. Je také nainstalován automaticky, když zvolíte součást **Programu Connection Manager** v instalačním programu. Je nainstalován v *souboru\\%VCIDEInstallDir% Linux\\\\\\bin ConnectionManagerExe ConnectionManager.exe*.

Funkce connectionmanager.exe je k dispozici také v sadě Visual Studio. Chcete-li spravovat vzdálená vývojová připojení v prostředí IDE, zvolte na řádku nabídek **možnostI** > **nástroje** a otevřete dialogové okno Možnosti. V dialogovém okně Možnosti vyberte **položku Cross Platform** > **Connection Manager**.

## <a name="syntax"></a>Syntaxe

> *Argumenty* *příkazů* \[ **ConnectionManager.exe** ] \[ *možnosti*]

### <a name="commands-and-arguments"></a>Příkazy a argumenty

- **přidání** *\@uživatelského hostitele* \[ \[ **--port** *port*] **--heslo** *heslo* \[] **--privatekey** *privatekey_file*]

  Ověří a přidá nové připojení. Ve výchozím nastavení používá port 22 a ověřování hesla. (Budete vyzváni k zadání hesla.) K zadání hesla soukromého klíče použijte **--password** a **--privatekey.**

- **odebrat** \[ *connection_id* \| *hostiteli\@* \[ **uživatele --port** *]]*

  Odebere připojení. Pokud nejsou zadány žádné argumenty, budete vyzváni k určení, které připojení chcete odebrat.

- **odstranit vše**

  Odebere všechna uložená připojení.

- **list**

  Zobrazí informace a ID všech uložených připojení.

- **Pomoc**

  Zobrazí obrazovku nápovědy.

- **Verze**

  Zobrazí informace o verzi.

### <a name="options"></a>Možnosti

- **-q**, **--ticho**

  Zabraňuje výstupu `stdout` nebo `stderr`.

- **--no-prompt**

  Pokud je to vhodné, selžte místo výzvy.

- **--no-verify**

  Přidání nebo úprava připojení bez ověření.

- **--název** *souboru*

  Přečtěte si informace o připojení z poskytnutého *názvu souboru*.

- **--no-telemetrie**

  Zakažte odesílání dat o využití zpět společnosti Microsoft. Data o využití jsou shromažďována a odesílána zpět společnosti Microsoft, pokud není předán příznak **--no-telemetric.**  

- **-n**, **--běh na suchu**

  Má suchý běh příkazu.

- **-p**

  Stejné jako **--password**.

- **-i**

  Stejné jako **--privatekey**.

## <a name="examples"></a>Příklady

Tento příkaz přidá připojení pro uživatele s názvem "uživatel" na localhost. Připojení používá k ověření soubor klíče, který se nachází v *%USERPROFILE%\.ssh\id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Tento příkaz odebere připojení, které má ID 1975957870 ze seznamu připojení.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Viz také

[Připojení k cílovému systému Linux ve Visual Studiu](connect-to-your-remote-linux-computer.md)

::: moniker-end
