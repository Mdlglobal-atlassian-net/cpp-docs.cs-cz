---
title: Odkaz ConnectionManager
ms.date: 01/17/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 2b01bfbcd81984e7ddf32cd5ab0485fff17b3d2b
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520898"
---
# <a name="connectionmanager-reference"></a>Odkaz ConnectionManager

::: moniker range="<=vs-2017"

Soubor ConnectionManager. exe je k dispozici v aplikaci Visual Studio 2019 verze 16,5 a novější.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager. exe je nástroj příkazového řádku pro správu připojení vzdáleného vývoje mimo sadu Visual Studio. Je vhodný pro úlohy, jako je například zřízení nového vývojového počítače. Nebo ho použijte k nastavení sady Visual Studio pro průběžnou integraci. Můžete ho použít v Developer Command Promptm okně. Další informace o Developer Command Prompt najdete v tématu [použití sady nástrojů Microsoft C++ z příkazového řádku](..\build\building-on-the-command-line.md).

Soubor ConnectionManager. exe je k dispozici v aplikaci Visual Studio 2019 verze 16,5 a novější. Je součástí **vývoje pro Linux s C++**  úlohou v instalační program pro Visual Studio. Také se nainstaluje automaticky při výběru komponenty **Správce připojení** v instalačním programu. Instaluje se do *% VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager. exe*.

Funkce nástroje ConnectionManager. exe je také k dispozici v aplikaci Visual Studio. Chcete-li spravovat připojení vzdáleného vývoje v integrovaném vývojovém prostředí, v panelu nabídek vyberte možnost **nástroje** > **Možnosti** . otevře se dialogové okno Možnosti. V dialogovém okně Možnosti vyberte pro **různé platformy** > **Správce připojení**.

## <a name="syntax"></a>Syntaxe

> **ConnectionManager. exe** *příkaz* \[*argumenty*] \[*Možnosti*]

### <a name="commands-and-arguments"></a>Příkazy a argumenty

- **Přidat** *uživatele\@hostitele* \[ **--port portu** *]* \[ **--** heslo *heslo*] \[ **--PrivateKey** *privatekey_file*]

  Ověří a přidá nové připojení. Ve výchozím nastavení používá port 22 a ověřování hesla. (Zobrazí se výzva k zadání hesla.) Pro zadání hesla privátního klíče použijte jak **hesla** , tak i **--PrivateKey** .

- **odebrat** \[*connection_id* \| *uživatel\@hostitel* \[ **--** *port*portu]]

  Odebere připojení. Pokud nejsou zadány žádné argumenty, budete vyzváni k zadání připojení, které chcete odebrat.

- **Odebrat – vše**

  Odebere všechna uložená připojení.

- **list**

  Zobrazí informace a ID všech uložených připojení.

- **Pomoc**

  Zobrazí obrazovku help.

- **version**

  Zobrazí informace o verzi.

### <a name="options"></a>Možnosti

- **-q**, **--quiet**

  Brání výstupům `stdout` nebo `stderr`.

- **--bez výzvy**

  V případě potřeby selže místo výzvy.

- **--bez ověřování**

  Přidání nebo úprava připojení bez ověřování.

- **--** *filename* souboru

  Načte informace o připojení ze zadaného *názvu souboru*.

- **--No-telemetrie**

  Zakázat odesílání dat o využití zpět společnosti Microsoft. Data o využití se shromažďují a odesílají zpátky společnosti Microsoft, pokud není předán příznak **--No-telemetrie** .  

- **-n**, **--suchý-běh**

  Provede suché spuštění příkazu.

- **-p**

  Stejné jako **--Password**.

- **-i**

  Stejné jako **--PrivateKey**.

## <a name="examples"></a>Příklady

Tento příkaz přidá připojení uživatele s názvem "User" na localhost. Připojení používá soubor klíče pro ověřování, který se nachází v *% USERPROFILE%\.SSH \ id_rsa*.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

Tento příkaz odebere ze seznamu připojení připojení, které má ID 1975957870.

```cmd
ConnectionManager.exe remove 1975957870
```

## <a name="see-also"></a>Viz také:

[Připojení k cílovému systému Linux v aplikaci Visual Studio](connect-to-your-remote-linux-computer.md)

::: moniker-end
