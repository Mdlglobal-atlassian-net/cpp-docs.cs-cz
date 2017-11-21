---
title: "Editor řetězce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.string.F1
dev_langs: C++
helpviewer_keywords:
- String editor
- string tables
- string tables, String editor
- string editing
- string editing, string tables
- resource editors, String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a84ee72d44a7c7ba694df023ad50258513b40bf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="string-editor"></a>Editor řetězce
Tabulky řetězců je prostředek systému Windows, který obsahuje seznam ID, hodnoty a titulky pro všechny řetězce vaší aplikace. Například výzvy stavového řádku jsou umístěny v tabulce řetězců.  
  
 Při vývoji aplikace, může mít několik tabulek řetězců – jeden pro každou jazyka nebo podmínky. Spustitelný soubor modulu má však pouze jednu tabulku řetězec. Spuštěné aplikace můžete odkazovat několik tabulek řetězců, když vložíte do různých knihoven DLL tabulky.  
  
 Tabulky řetězců usnadní lokalizaci vaší aplikace do různých jazyků. Pokud všechny řetězce jsou v tabulce řetězce, je možné lokalizovat aplikace beze změny zdrojového kódu při převodu řetězce (a další prostředky). Toto je obvykle žádoucí více než ručně hledání a nahrazování řetězců různé ve zdrojových souborech.  
  
 Pomocí editoru řetězec, můžete:  
  
-   [Vyhledávání pro jeden nebo více řetězců](../windows/finding-a-string.md).  
  
-   Rychle [vložit nové položky](../windows/adding-or-deleting-a-string.md) do tabulky řetězec.  
  
-   [Přesunutí řetězce z jednoho zdrojového souboru do jiného](../windows/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [Použít místní úpravy vlastností ID, hodnotu a titulek](../windows/changing-the-properties-of-a-string.md) a zobrazit změny okamžitě.  
  
-   [Změna vlastnosti titulku vícenásobných řetězců](../windows/changing-the-caption-property-of-multiple-strings.md)  
  
-   [Přidání formátovacích nebo speciálních znaků do řetězce](../windows/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Nepovoluje Windows vytváření tabulek prázdný řetězec. Pokud vytvoříte tabulku řetězec s žádné položky, odstraní se automaticky při ukládání souboru prostředků.  
  
 Informace o přidávání zdrojů do spravovaných projekty (ty, které cílí modul common language runtime), najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti, najdete v části [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití zdrojů pro lokalizaci s technologií ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)   
 [Řetězce](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [O řetězcích](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)

