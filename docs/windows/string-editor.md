---
title: Editor řetězců | Dokumentace Microsoftu
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
- string tables, String editor
- string editing
- string editing, string tables
- resource editors, String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 51470a572ec9540f203bb4cff80981fe6ad15dd1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578568"
---
# <a name="string-editor"></a>Editor řetězce

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

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití prostředků for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)  
[Řetězce](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)  
[O řetězcích](/windows/desktop/menurc/about-strings)

