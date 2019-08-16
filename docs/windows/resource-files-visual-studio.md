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
ms.openlocfilehash: b66a207766962856cc4d7181607868c2a48ebe84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513656"
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)

> [!NOTE]
> Vzhledem k tomu, že projekty v programovacích jazycích .NET nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumník řešení**. Použijte [Editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech.
>
> Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Termínový *soubor prostředků* může odkazovat na určitý počet typů souborů, například:

- Soubor skriptu prostředků (. RC) programu.

- Soubor šablony prostředků (. RCT).

- Jednotlivý prostředek existuje jako samostatný soubor. Tento typ zahrnuje rastrový obrázek, ikonu nebo soubor kurzoru, který je odkazován ze souboru. rc.

- Hlavičkový soubor generovaný vývojovým prostředím. Tento typ zahrnuje `Resource.h`, je odkazováno ze souboru. rc.

Prostředky nalezené v jiných typech souborů, jako je například. exe,. dll nebo soubory. res, jsou označovány jako *prostředky*.

Můžete pracovat se *soubory prostředků* a *prostředky* v rámci projektu. Můžete také pracovat s těmi, které nejsou součástí aktuálního projektu nebo byly vytvořeny mimo vývojové prostředí sady Visual Studio. Můžete například:

- Pracujte s vnořenými a podmíněně zahrnutými soubory prostředků.

- Aktualizujte stávající prostředky nebo je převeďte C++na vizuál.

- Importujte nebo exportujte grafické prostředky do nebo z aktuálního souboru prostředků.

- Zahrňte sdílené nebo identifikátory (symboly) jen pro čtení, které nelze upravovat ve vývojovém prostředí.

- Zahrňte prostředky do spustitelného souboru (. exe), který nepotřebuje úpravy (nebo by se neměly upravovat), například sdílené prostředky mezi několika projekty.

- Zahrňte typy prostředků, které nejsou podporovány vývojovým prostředím.

Další informace o prostředcích najdete v tématech [vytváření prostředků](../windows/how-to-create-a-resource-script-file.md), [Správa prostředků](../windows/how-to-copy-resources.md)a [zahrnutí prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Upravitelné prostředky

Pro úpravu prostředků, které obsahují, lze otevřít následující typy souborů:

| Název souboru | Popis |
|---|---|
| .rc | Soubory skriptu prostředků |
| . RCT | Soubory šablon prostředků |
| . res | Soubory prostředků |
| .resx | Spravované soubory prostředků |
| soubor. exe | Spustitelné soubory |
| .dll | Soubory s dynamickou propojenou knihovnou |
| . bmp,. ico,. DIB,. měna | Rastrové obrázky, ikony, panely nástrojů a soubory kurzoru |

Při úpravách prostředků funguje prostředí sady Visual Studio s a má vliv na následující soubory:

| Název souboru | Popis |
|---|---|
| Resource.h | Hlavičkový soubor generovaný vývojovým prostředím, které obsahuje definice symbolů.<br/><br/>Zahrnout tento soubor do správy zdrojového kódu. |
| Filename.aps | Binární verze aktuálního souboru skriptu prostředku, která se používá pro rychlé načítání.<br /><br /> Editory prostředků nečtou přímo soubory. RC nebo Resource. h. Kompilátor prostředků je zkompiluje do souborů. APS, které jsou spotřebovány editory prostředků. Tento soubor je krok kompilace a ukládá pouze symbolické údaje.<br/><br/>Stejně jako u normálního procesu kompilace jsou informace, které nejsou symbolické, jako je například komentování, během procesu kompilace zahozeny.<br/><br/>Pokaždé, když soubor. APS není synchronizován se souborem. RC, bude soubor. RC znovu vygenerován. Když například **uložíte**, editor prostředků přepíše soubor. RC a soubor Resource. h. Jakékoli změny samotných prostředků zůstanou začleněny do souboru. RC, ale komentáře budou vždy ztraceny, jakmile bude soubor. RC přepsán. Informace o tom, jak zachovat komentáře, najdete v tématu [zahrnutí prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>Obvykle byste neměli do správy zdrojových kódů zahrnout soubor. APS. |
| .rc | Soubor skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Soubor. APS se při každém uložení přepíše souborem. AP.<br/><br/>Zahrnout tento soubor do správy zdrojového kódu. |

## <a name="manifest-resources"></a>Manifest prostředků

V C++ desktopových projektech jsou prostředky MANIFESTU soubory XML, které popisují závislosti, které aplikace používá. Například v aplikaci Visual Studio tento soubor manifestu generovaný průvodcem určuje, která verze knihoven DLL běžných ovládacích prvků systému Windows by měla aplikace používat:

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

V případě aplikace systému Windows XP nebo Windows Vista by měl prostředek manifestu určovat nejaktuálnější verzi běžných ovládacích prvků systému Windows, které má aplikace používat. Výše uvedený příklad používá verzi `6.0.0.0`, která podporuje [ovládací prvek Syslink](/windows/win32/Controls/syslink-overview).

> [!NOTE]
> Pro každý modul můžete mít jenom jeden prostředek manifestu.

Chcete-li zobrazit verzi a informace o typu obsažené v prostředku manifestu, otevřete soubor v prohlížeči XML nebo v textovém editoru sady Visual Studio. Otevřete-li prostředek manifestu z [prostředky](../windows/resource-view-window.md), bude prostředek otevřen v binárním formátu.

### <a name="to-open-a-manifest-resource"></a>Otevření prostředku manifestu

1. Otevřete projekt v aplikaci Visual Studio a přejděte na **Průzkumník řešení**.

1. Rozbalte složku **soubory prostředků** a potom:

   - Chcete-li otevřít v textovém editoru, poklikejte na soubor *. manifest* .

   - Chcete-li otevřít v jiném editoru, klikněte pravým tlačítkem myši na soubor *. manifest* a vyberte možnost **otevřít v**. Zadejte editor, který se má použít, a vyberte **otevřít**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Identifikátory prostředků (symboly)](../windows/symbols-resource-identifiers.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>