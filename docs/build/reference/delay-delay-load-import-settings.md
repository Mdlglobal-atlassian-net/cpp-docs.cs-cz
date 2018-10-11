---
title: -DELAY (nastavení importu odloženého načtení) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 086fab7d1d50f96ab05c38f2e6d524d7ff344e02
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081913"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (nastavení importu odloženého načtení)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Poznámky

Ovládací prvky/delay – možnost [s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md) knihoven DLL:

- Kvalifikátor UNLOAD přikazuje odloženě zaváděné pomocnou funkci, aby podporovala explicitní uvolnění knihovny DLL. Tabulky importu adres (IAT) je nastaven na původní podobě, proto už není platná IAT ukazatele a způsobuje přepsán.

   Pokud nevyberete uvolnění, žádném volání [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) se nezdaří.

- Kvalifikátor NOBIND přikazuje linkeru, aby do finální image zahrnout IAT s možností vazby. Ve výchozím nastavení je vytvořit IAT s možností vazby pro odloženě zaváděné knihovny DLL. Výsledná bitová kopie nemůže být vázán staticky. (Imagí pomocí umožňujících vazbu IATs staticky vázat před provedením.) Zobrazit [/BIND](../../build/reference/bind.md).

   Pokud je vázán knihovnu DLL, pomocná funkce se pokusí použít vázané informace namísto volání metody [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) ve všech odkazovaných importy. Pokud časové razítko nebo upřednostňovanou adresu neodpovídá načtené knihovny DLL, bude předpokládat pomocnou funkci vázané IAT je zastaralá a bude pokračovat, jako kdyby vázané IAT neexistuje.

   NOBIND způsobí, že váš program obrázku větší, ale můžete urychlit načítání času knihovny DLL. Pokud chcete nikdy vytvořit vazbu knihovny DLL, NOBIND zabrání vázané IAT nefunkční.

Pokud chcete zadat knihovny DLL pro odložené načtení, použijte [/delayload](../../build/reference/delayload-delay-load-import.md) možnost.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **Linkeru**a pak vyberte **Upřesnit**.

1. Upravit **knihovny DLL načtené se zpožděním** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)