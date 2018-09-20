---
title: Editor řetězců (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string.F1
dev_langs:
- C++
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 02248c7c6f61823649d9643a7321677e23a4afbf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382905"
---
# <a name="string-editor-c"></a>Editor řetězců (C++)

Tabulka řetězců je prostředek Windows, který obsahuje seznam ID, hodnoty a popisky pro všechny řetězce vaší aplikace. Například výzvy stavový řádek jsou umístěny v tabulce řetězců.

Při vývoji aplikace, máte několik tabulek řetězců, jeden pro každý jazyk nebo podmínku. Spustitelný soubor modulu má však pouze jedna tabulka řetězců. Běžící aplikaci může odkazovat několik tabulek řetězců, pokud vložené tabulky do jiné knihovny DLL.

Tabulky řetězců umožňují snadno lokalizovat vaši aplikaci do různých jazyků. Pokud jsou všechny řetězce v tabulce řetězců, je možné lokalizovat aplikaci při převodu řetězce (a další prostředky) bez změny zdrojového kódu. Toto je obvykle žádoucí více než ručně vyhledávání a nahrazování různých řetězců ve zdrojových souborech.

Pomocí editoru řetězce, můžete:

- [Hledání řetězců jeden nebo více](../windows/finding-a-string.md).

- Rychle [vložit nové položky](../windows/adding-or-deleting-a-string.md) do tabulky řetězců.

- [Přesunutí řetězce z jednoho zdrojového souboru do druhého](../windows/moving-a-string-from-one-resource-file-to-another.md)

- [Použít místní úpravy. pro vlastnosti ID, hodnotu a popisek](../windows/changing-the-properties-of-a-string.md) a podívejte se na změny okamžitě.

- [Změna vlastnosti titulku vícenásobných řetězců](../windows/changing-the-caption-property-of-multiple-strings.md)

- [Přidání formátovacích nebo speciálních znaků do řetězce](../windows/adding-formatting-or-special-characters-to-a-string.md)

   > [!NOTE]
   > Windows neumožňuje vytvoření tabulky prázdný řetězec. Pokud vytvoříte tabulku řetězců s žádné položky, odstraní se automaticky při ukládání souboru prostředků.

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Řetězce](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[O řetězcích](/windows/desktop/menurc/about-strings)

