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
ms.openlocfilehash: 4d56a62dfa350b3113a28355433130563464c6be
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320533"
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)

> [!NOTE]
> Protože projekty v programovacích jazycích rozhraní .NET nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Termín "soubor prostředků" mohou odkazovat na několik typů souborů, včetně:

- Soubor skriptu prostředků (.rc) programu.

- Soubor prostředků šablony (.rct).

- Samostatný prostředek existující jako samostatný soubor, například soubor bitmapy, ikony nebo kurzoru to je odkazováno ze souboru .rc.

- Soubor hlaviček generovaných vývojové prostředí, například Resource.h, které je uvedené v souboru .rc.

Prostředky jsou taky součástí jiné typy souborů, jako je například .exe, .dll a soubory .res. Můžete pracovat s prostředky a soubory prostředků z v rámci vašeho projektu a ty, které nejsou součástí aktuálního projektu. Můžete také pracovat se soubory prostředků, které nebyly vytvořeny ve vývojovém prostředí sady Visual Studio. Například můžete:

- Práce se soubory prostředků vnořené a podmíněně zahrnuté.

- Aktualizovat stávající prostředky nebo je převést na formát Visual C++.

- Import a export grafických prostředků do nebo z aktuálního zdrojového souboru.

- Zahrnutí sdílených nebo jen pro čtení identifikátorů (symbolů), které nelze upravit ve vývojovém prostředí.

- Zahrnout zdroje v souboru spustitelný soubor (.exe), které nevyžadují úpravy (nebo by neměla být upravována) během aktuálního projektu, jako jsou například prostředky sdílené mezi několika projekty.

- Zahrnují typy prostředků nejsou podporovány ve vývojovém prostředí.

Tato část popisuje postup:

- [Vytvoření prostředků](../windows/how-to-create-a-resource-script-file.md)

- [Správa prostředků](../windows/how-to-copy-resources.md)

- [Zahrnutí prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md)

## <a name="editable-resource-file-types"></a>Typy souborů prostředků upravitelné

Chcete-li upravit prostředky, které obsahují lze otevřít následující typy souborů:

|Název souboru|Popis|
|---------|-----------------|
|.rc|Soubory skriptu prostředků|
|.RCT|Soubory šablon prostředků|
|.res|Soubory prostředků|
|.resx|Spravovaných souborů prostředků|
|.exe|Spustitelné soubory|
|.dll|Soubory knihoven DLL|
|.bmp, ICO, DIB a .cur|Rastrový obrázek, ikona, nástrojů a kurzoru soubory.|

Prostředí sady Visual Studio spolupracuje s a ovlivňuje během váš prostředek relace úprav následující soubory:

|Název souboru|Popis|
|---------------|-----------------|
|Resource.h|Soubor hlaviček generovaných vývojové prostředí; obsahuje definice symbolů. (Zahrnout tento soubor do správy zdrojového kódu.)|
|Filename.aps|Binární verze aktuálního souboru skriptu prostředků; používá se pro rychlé načítání.<br /><br /> Editory prostředků není přímo načíst soubory .rc nebo souboru resource.h. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a soubor resource.h). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [zahrnout prostředky v době kompilace](../windows/how-to-include-resources-at-compile-time.md). (Obvykle, nezahrnujte .aps soubor ve správě zdrojového kódu.)|
|.rc|Soubor skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Tento soubor se přepíše souborem .aps při každém uložení. (Zahrnout tento soubor do správy zdrojového kódu.)|

## <a name="manifest-resources"></a>Manifest prostředků

Prostředky manifestu v desktopové projekty C++, jsou soubory XML, které popisují závislosti, které aplikace používá. Například v sadě Visual Studio manifestu soubor generované průvodcem MFC definuje které verze 5.0 nebo 6.0, Windows běžný ovládací prvek aplikace by měla používat knihovny DLL:

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

Pro aplikace Windows XP nebo Windows Vista prostředku manifestu nejen Určuje, že aplikace používat nejnovější verzi běžných ovládacích prvků Windows, verze 6.0, jak je znázorněno výše, ale také podporuje [ovládací prvek Syslink](/windows/desktop/Controls/syslink-overview).

K zobrazení verze a typ informací obsažených v manifestu prostředek, můžete otevřít soubor v prohlížeči XML nebo textovém editoru sady Visual Studio. Otevření prostředku manifestu z [zobrazení prostředků](../windows/resource-view-window.md), prostředek se otevře v binárním formátu. Chcete-li zobrazit obsah manifestu prostředek ve formátu více zobrazitelné, je nutné otevřít prostředek z **Průzkumníka řešení**.

### <a name="to-open-a-manifest-resource"></a>K otevření prostředku manifestu

1. Otevřete svůj projekt v sadě Visual Studio.

1. Přejděte do **Průzkumníka řešení** a rozbalte **soubory prostředků** složky.

   - Textový editor dvakrát klikněte na soubor .manifest.

   - Pro jiné editory, klikněte pravým tlačítkem na soubor .manifest a vyberte **otevřít v programu...** , pak zadejte editor k použití a zvolte **otevřít**.

> [!NOTE]
> Můžete mít jenom jeden prostředek manifestu na modul.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Identifikátory prostředků (symbolů)](../windows/symbols-resource-identifiers.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>