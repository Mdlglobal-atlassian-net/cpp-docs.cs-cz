---
title: Zdrojové soubory (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 65500644b70841f372edcc6911edefc6c7b9f432
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152687"
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)

> [!NOTE]
> Tento materiál se vztahuje na aplikace klasické pracovní plochy Windows. Informace o prostředcích v aplikacích pro univerzální platformu Windows, naleznete v tématu [definování prostředků aplikace](/windows/uwp/app-resources/).
>
> Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).
>
> Protože projekty v programovacích jazycích rozhraní .NET nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Termín "soubor prostředků" mohou odkazovat na několik typů souborů, včetně:

- Soubor skriptu prostředků (.rc) programu.

- Soubor prostředků šablony (.rct).

- Samostatný prostředek existující jako samostatný soubor, například soubor bitmapy, ikony nebo kurzoru to je odkazováno ze souboru .rc.

- Soubor hlaviček generovaných vývojové prostředí, například Resource.h, které je uvedené v souboru .rc.

Prostředky jsou taky součástí [jiné typy souborů](../windows/editable-file-types-for-resources.md) například soubory .exe, .dll a Res. Můžete pracovat s prostředky a soubory prostředků z v rámci vašeho projektu a ty, které nejsou součástí aktuálního projektu. Můžete také pracovat se soubory prostředků, které nebyly vytvořeny ve vývojovém prostředí sady Visual Studio. Například můžete:

- Práce se soubory prostředků vnořené a podmíněně zahrnuté.

- Aktualizovat stávající prostředky nebo je převést na formát Visual C++.

- Import a export grafických prostředků do nebo z aktuálního zdrojového souboru.

- Zahrnutí sdílených nebo jen pro čtení identifikátorů (symbolů), které nelze upravit ve vývojovém prostředí.

- Zahrnout zdroje v souboru spustitelný soubor (.exe), které nevyžadují úpravy (nebo by neměla být upravována) během aktuálního projektu, jako jsou například prostředky sdílené mezi několika projekty.

- Zahrnují typy prostředků nejsou podporovány ve vývojovém prostředí.

Můžete otevřít následující typy souborů a upravit prostředky, které obsahují:

|Název souboru|Popis|
|---------------|-----------------|
|.rc|Soubory skriptu prostředků.|
|.RCT|Soubory prostředků šablon.|
|.res|Soubory prostředků.|
|.resx|Spravovaných zdrojových souborů.|
|.exe|Spustitelné soubory.|
|.dll|Soubory knihoven DLL.|
|.bmp, ICO, DIB a .cur|Rastrový obrázek, ikona, nástrojů a kurzoru soubory.|

Prostředí sady Visual Studio spolupracuje s a ovlivňuje soubory uvedené v následující tabulce během úprav relace prostředků:

|Název souboru|Popis|
|---------------|-----------------|
|Resource.h|Soubor hlaviček generovaných vývojové prostředí; obsahuje definice symbolů. (Zahrnout tento soubor do správy zdrojového kódu.)|
|Filename.aps|Binární verze aktuálního souboru skriptu prostředků; používá se pro rychlé načítání.<br /><br /> Editory prostředků není přímo načíst soubory .rc nebo souboru resource.h. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a soubor resource.h). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md). (Obvykle, nezahrnujte .aps soubor ve správě zdrojového kódu.)|
|.rc|Soubor skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Tento soubor se přepíše souborem .aps při každém uložení. (Zahrnout tento soubor do správy zdrojového kódu.)|

Tato část popisuje postup:

- [Vytvoření prostředků](../windows/how-to-create-a-resource-script-file.md)

- [Správa prostředků](../windows/how-to-copy-resources.md)

- [Zahrnutí prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md)

## <a name="manifest-resources"></a>Prostředky manifestu

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

K otevření prostředku manifestu, zvolte z následujících kroků:

- Pro váš projekt otevřít v textovém editoru **Průzkumníka řešení**, rozbalte **soubory prostředků** složky a poklikejte na soubor .manifest.

- Pro jiný editor v **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor .manifest a zvolte **otevřít v programu...**  z místní nabídky. V **otevřít v** dialogovém okně zadejte editor, který chcete použít a vyberte **otevřít**.

> [!NOTE]
> Můžete mít jenom jeden prostředek manifestu na modul.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Nabídky a ostatní prostředky](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)<br/>