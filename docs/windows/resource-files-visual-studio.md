---
title: Zdrojové soubory (C++)
ms.date: 11/04/2016
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
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 9ad36f19185bc5b3430e7644ef55164d3cb0839a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461693"
---
# <a name="resource-files-c"></a>Zdrojové soubory (C++)

> [!NOTE]
> Tento materiál se vztahuje na aplikace klasické pracovní plochy Windows. Informace o prostředcích v aplikacích pro univerzální platformu Windows, naleznete v tématu [definování prostředků aplikace](/windows/uwp/app-resources/).
>
> Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).
>
> Protože projekty v programovacích jazycích rozhraní .NET nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Termín "soubor prostředků" mohou odkazovat na několik typů souborů, včetně:

- Soubor skriptu prostředků (.rc) programu.

- Soubor prostředků šablony (.rct).

- Samostatný prostředek existující jako samostatný soubor, například soubor bitmapy, ikony nebo kurzoru to je odkazováno ze souboru .rc.

- Soubor hlaviček generovaných vývojové prostředí, například Resource.h, které je uvedené v souboru .rc.

Prostředky můžete najít také v [jiné typy souborů](../windows/editable-file-types-for-resources.md) například soubory .exe, .dll a Res. Můžete pracovat s prostředky a soubory prostředků z v rámci vašeho projektu a s těmi, které nejsou součástí aktuálního projektu. Můžete také pracovat se soubory prostředků, které nebyly vytvořeny ve vývojovém prostředí sady Visual Studio. Například můžete:

- Práce se soubory prostředků vnořené a podmíněně zahrnuté.

- Aktualizovat stávající prostředky nebo je převést na formát Visual C++.

- Import a export grafických prostředků do nebo z aktuálního zdrojového souboru.

- Zahrnutí sdílených nebo jen pro čtení identifikátorů (symbolů), které nelze upravit ve vývojovém prostředí.

- Zahrnout zdroje v souboru spustitelný soubor (.exe), které nevyžadují úpravy (nebo které nechcete upravovat) během vašeho aktuálního projektu, jako jsou například prostředky, které se sdílejí mezi několika projekty.

- Zahrnují typy prostředků nejsou podporovány ve vývojovém prostředí.

Tato část zahrnuje:

- [Vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md)

- [Vytváří se nový prostředek](../windows/how-to-create-a-resource.md)

- [Zobrazování prostředků v souboru skriptu prostředků](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)

- [Otevření souboru skriptu prostředků v textovém formátu](../windows/how-to-open-a-resource-script-file-in-text-format.md)

- [Včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md)

- [Kopírování prostředků](../windows/how-to-copy-resources.md)

- [Použití šablon prostředků (.rct)](../windows/how-to-use-resource-templates.md)

- [Import a export prostředků](../windows/how-to-import-and-export-resources.md)

- [Upravitelné typy souborů pro prostředky](../windows/editable-file-types-for-resources.md)

- [Soubory ovlivněné úpravou prostředku](../windows/files-affected-by-resource-editing.md)

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Nabídky a ostatní prostředky](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)