---
title: /TSAWARE (Vytvořit aplikace s detekcí terminálového serveru)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: 981158125cf978c2f685501117f95553df9c3c89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498189"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Vytvořit aplikace s detekcí terminálového serveru)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Poznámky

Možnost/TSAWARE nastaví příznak v poli IMAGE_OPTIONAL_HEADER DllCharacteristics v volitelné hlavičce obrázku programu. Pokud je tento příznak nastaven, terminálový server neprovede určité změny aplikace.

Pokud aplikace nepoužívá terminálový server (označuje se také jako starší verze aplikace), Terminálový Server provede určité změny v rámci starší verze aplikace, aby fungovaly správně ve víceuživatelském prostředí. Například terminálový server vytvoří virtuální složku systému Windows, takže každý uživatel získá složku systému Windows namísto získání adresáře systému Windows. To uživatelům umožňuje přístup k vlastním souborům INI. Kromě toho Terminálový Server provede několik úprav v registru pro starší verzi aplikace. Tyto úpravy zpomalují načítání starší verze aplikace na terminálovém serveru.

Pokud aplikace používá Terminálový Server, nesmí ani spoléhat na soubory INI ani zapisovat do registru **HKEY_CURRENT_USER** během instalace.

Pokud používáte/TSAWARE a vaše aplikace stále používá soubory INI, soubory budou sdíleny všemi uživateli systému. Pokud je to přijatelné, můžete i nadále propojit aplikaci s/TSAWARE; v opačném případě je nutné použít/TSAWARE: NO.

Možnost/TSAWARE je ve výchozím nastavení povolená pro aplikace pro Windows a konzolové aplikace. Informace najdete v tématu [/Subsystem](subsystem-specify-subsystem.md) a [/Version](version-version-information.md) .

/TSAWARE není platný pro ovladače, VxDs nebo knihovny DLL.

Pokud byla aplikace propojená s/TSAWARE, zobrazí se v tomto efektu DUMPBIN [/Headers](headers.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **linker** .

1. Klikněte na stránku vlastnost **systému** .

1. Upravte vlastnost **terminálového serveru** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[Ukládání informací specifických pro uživatele](/windows/win32/TermServ/storing-user-specific-information)<br/>
[Starší verze aplikací v prostředí Terminálové služby](https://msdn.microsoft.com/library/aa382957.aspx)
