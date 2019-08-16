---
title: /DELAY (nastavení importu odloženého načtení)
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492998"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (nastavení importu odloženého načtení)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Poznámky

Možnost/DELAY řídí [opožděné načítání](linker-support-for-delay-loaded-dlls.md) knihoven DLL:

- Kvalifikátor Unload oznamuje funkci opožděného načítání, aby podporovala explicitní uvolnění knihovny DLL. Tabulka importních adres (IAT) je resetována na původní formulář, který neověřuje ukazatele IAT a způsobuje jejich přepsání.

   Pokud nevyberete možnost uvolnění, žádné volání [FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md) se nezdaří.

- Kvalifikátor IAT přikáže linkeru, aby nezahrnoval s možností vazby v konečné imagi. Výchozím nastavením je vytvoření IAT s možností vazby pro odložené načítání knihoven DLL. Výsledný obrázek nelze staticky svázat. (Obrázky s IATs s možností vazby můžou být před spuštěním staticky svázané.) Viz [/BIND](bind.md).

   Pokud je knihovna DLL vázána, pomocná funkce se pokusí použít vázané informace namísto volání funkce [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) u každého odkazovaného importu. Pokud buď časové razítko nebo Upřednostňovaná adresa neodpovídá hodnotám načtených knihoven DLL, pomocná funkce bude předpokládat, že vázaný IAT je zastaralá a bude pokračovat, jako kdyby vazba IAT neexistuje.

   Při nevytváření vazby dojde k většímu množství obrázku programu, ale může to urychlit načítání knihovny DLL. Pokud nikdy nechcete svázat knihovnu DLL, nevytvoří se vazba IAT, aby se vytvořila vazba.

K určení knihoven DLL pro odložené načtení použijte možnost [/DELAYLOAD](delayload-delay-load-import.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte položku **Vlastnosti konfigurace**, **linker**a pak vyberte **Upřesnit**.

1. Upravte vlastnost **odložené načtení knihovny DLL** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
