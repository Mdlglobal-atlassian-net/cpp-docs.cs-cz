---
title: Zdrojové soubory (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 45db6d0139cfa3aa8a2eaa8fe6d18158cb6646ce
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029392"
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)

> [!NOTE]
> Protože projekty v programovacích jazycích rozhraní .NET nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Použití [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech.
>
> Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Termín *soubor prostředků* může odkazovat několik typů souborů, jako je třeba:

- Soubor skriptu prostředků (.rc) programu.

- Soubor prostředků šablony (.rct).

- Samostatný prostředek existující jako samostatný soubor. Tento typ zahrnuje bitmapy, ikony nebo kurzoru soubor, který je uvedené v souboru .rc.

- Soubor hlaviček generovaných vývojové prostředí. Tento typ zahrnuje `Resource.h`, to je odkazováno ze souboru .rc.

Prostředky se nenašly v jiné typy souborů, jako jsou soubory .exe, .dll a .res označovány jako *prostředky*.

Můžete pracovat s *soubory prostředků* a *prostředky* z v rámci svého projektu. Můžete také pracovat s, které nejsou součástí aktuálního projektu nebo byly vytvořeny mimo vývojové prostředí sady Visual Studio. Například můžete:

- Práce se soubory prostředků vnořené a podmíněně zahrnuté.

- Aktualizovat existující prostředky nebo jejich převodem na Visual C++.

- Import a export grafických prostředků do nebo z aktuálního zdrojového souboru.

- Zahrnutí sdílených nebo jen pro čtení identifikátorů (symbolů), které nelze upravit ve vývojovém prostředí.

- Zahrnout zdroje v souboru spustitelný soubor (.exe), který není třeba úpravy (nebo by neměla být upravována), jako jsou například prostředky sdílené mezi několika projekty.

- Zahrnují typy prostředků nejsou podporovány ve vývojovém prostředí.

Další informace o prostředcích naleznete v tématu Jak [vytvořit prostředky](../windows/how-to-create-a-resource-script-file.md), [spravovat prostředky](../windows/how-to-copy-resources.md), a [zahrnout prostředky v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Upravit prostředky

Chcete-li upravit prostředky, které obsahují lze otevřít následující typy souborů:

| Název souboru | Popis |
|---|---|
| .rc | Soubory skriptu prostředků |
| .RCT | Soubory šablon prostředků |
| .res | Soubory prostředků |
| .resx | Spravovaných souborů prostředků |
| .exe | Spustitelné soubory |
| .dll | Soubory knihoven DLL |
| .bmp, ICO, .dib, .cur | Rastrový obrázek, ikona, nástrojů a kurzoru soubory |

Při úpravě prostředků prostředí sady Visual Studio pracuje s a má vliv na následující soubory:

| Název souboru | Popis |
|---|---|
| Resource.h | Soubor hlaviček generovaných vývojové prostředí, která obsahuje definice symbolů.<br/><br/>Zahrnout tento soubor ve správě zdrojového kódu. |
| Filename.aps | Binární verze aktuálního souboru skriptu prostředků použít pro rychlé načítání.<br /><br /> Editory prostředků není přímo načíst soubory .rc nebo souboru resource.h. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické.<br/><br/>Jako normální zkompilovat procesu, informace, které nejsou symbolické, jako je například přidávání poznámek, je ignorována během kompilace.<br/><br/>Pokaždé, když je soubor .aps synchronizováno s soubor .rc, opakovaném vygenerování souboru .rc. Například, když jste **Uložit**, přepíše editor prostředků není soubor .rc a souboru resource.h. Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [zahrnout prostředky v době kompilace](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>Obvykle by neměla obsahovat .aps soubor ve správě zdrojového kódu. |
| .rc | Soubor skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Tento soubor se přepíše souborem .aps při každém uložení.<br/><br/>Zahrnout tento soubor ve správě zdrojového kódu. |

## <a name="manifest-resources"></a>Manifest prostředků

Prostředky manifestu v desktopové projekty C++, jsou soubory XML, které popisují závislosti, které aplikace používá. Například v sadě Visual Studio tento MFC soubor manifestu generované v Průvodci definuje verze Windows běžný ovládací prvek knihoven DLL aplikace by měla používat:

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Pro aplikace Windows XP nebo Windows Vista by měl prostředek manifestu zadejte nejaktuálnější verzi běžných ovládacích prvků Windows pro aplikace pro použití. Výše uvedený příklad používá verzi `6.0.0.0`, která podporuje [ovládací prvek Syslink](/windows/desktop/Controls/syslink-overview).

> [!NOTE]
> Můžete mít jenom jeden prostředek manifestu na modul.

Chcete-li zobrazit verze a typ informací obsažených v manifestu prostředek, otevřete soubor v prohlížeči XML nebo textovém editoru sady Visual Studio. Otevření prostředku manifestu z [zobrazení prostředků](../windows/resource-view-window.md), prostředek se otevře v binárním formátu.

### <a name="to-open-a-manifest-resource"></a>K otevření prostředku manifestu

1. Otevřete projekt v sadě Visual Studio a přejděte do **Průzkumníka řešení**.

1. Rozbalte **soubory prostředků** složku, pak:

   - Otevřít v textovém editoru, dvakrát klikněte *.manifest* souboru.

   - Otevřít v jiném editoru, klikněte pravým tlačítkem myši *.manifest* a vyberte možnost **otevřít v programu**. Zadejte editor k použití a vyberte **otevřít**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Identifikátory prostředků (symbolů)](../windows/symbols-resource-identifiers.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>