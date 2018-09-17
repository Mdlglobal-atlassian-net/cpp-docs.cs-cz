---
title: -TSAWARE (Vytvoření aplikace s terminálového serveru) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
dev_langs:
- C++
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac9aeaaf4ccaaf3f813adbf9f65eb3db7df353f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723943"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Vytvořit aplikace s detekcí terminálového serveru)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Poznámky

Parametr/TSAWARE nastaví příznak v poli IMAGE_OPTIONAL_HEADER dllcharacteristics v nepovinné hlavičce bitové kopie programu. Pokud je tento příznak nastaven, neprovede Terminálový Server určité změny aplikace.

Pokud aplikace není terminálového serveru Terminal (označované také jako starší verze aplikace), provede Terminálový Server určité změny starší verze aplikace, aby byla správně pracovat v prostředí. Terminálový Server například vytvoří virtuální složka Windows tak, aby každý uživatel získá složku Windows místo získávání adresáře v systému Windows. To poskytuje uživatelům přístup k vlastní soubory INI. Kromě toho Terminálový Server provede některé změny v registru pro starší verze aplikace. Tyto úpravy pomalé načítání starší verze aplikace v terminálového serveru.

Pokud aplikaci terminál terminálového serveru, musí, ani využívají soubory INI ani zapisovat **HKEY_CURRENT_USER** registru během instalace.

Pokud používáte parametr/TSAWARE a vaše aplikace stále používá soubory INI, budou všichni uživatelé systému sdílet soubory. Pokud je to přijatelné, můžete stále propojit aplikaci se parametr/TSAWARE; jinak budete muset použít podporu.

Parametr/TSAWARE je povolené ve výchozím nastavení pro Windows a konzolových aplikací. Zobrazit [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) a [/Version](../../build/reference/version-version-information.md) informace.

/ TSAWARE není platný pro ovladače, ovladače VxD nebo knihovny DLL.

Pokud byla aplikace propojené s parametr/TSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) se zobrazí informace o tom.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **systému** stránku vlastností.

1. Upravit **terminálového serveru** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[Ukládání informací specifických pro uživatele](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[Starší verze aplikace v prostředí Terminálové služby](https://msdn.microsoft.com/library/aa382957.aspx)