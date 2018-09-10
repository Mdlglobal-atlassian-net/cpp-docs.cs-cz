---
title: Vlastnosti příkazu nabídky (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menu items, properties
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 28426e2ca75638f5ad45188a8790d1c281afa99b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317913"
---
# <a name="menu-command-properties-c"></a>Vlastnosti příkazu nabídky (C++)

Níže uvedené informace jsou uspořádané podle **nabídky** vlastnosti, které se zobrazují v [okno vlastností](/visualstudio/ide/reference/properties-window) když vyberete příkaz nabídky. Ty jsou uvedeny v abecedním pořadí i když **vlastnosti** okna také umožňuje zobrazit tyto vlastnosti podle kategorie.

|Vlastnost|Popis|
|--------------|-----------------|
|**Konec**|Může být jedna z těchto hodnot:<br /><br /> -   **Žádný** (výchozí): žádné přerušení.<br />-   **Sloupec**: pro statické nabídky, tato hodnota umístí příkaz nabídky na nový řádek. Pro místní nabídky umístí tato hodnota příkazu nabídky nový sloupec s žádný zřejmý mezi sloupci. Nastavení této vlastnosti má vliv na vzhled nabídky pouze v době běhu, není v nabídce editoru.<br />-   **Panel**: totéž jako **sloupec** s výjimkou, pro místní nabídky, tato hodnota odděluje nového sloupce ze staré sloupci se zobrazuje svislá čára. Nastavení této vlastnosti není v ovlivňuje vzhled nabídky pouze v době běhu **nabídky** editoru.|
|**Titulek**|Text, který označuje příkaz nabídky (název nabídky). K výběru jedné ze písmena v popiscích nabídky příkazu mnemonická klávesa, předchází znak ampersand (&).|
|**Zaškrtnuto**|Pokud **True**, je příkaz nabídky hesla implicitně zaškrtnuto. Typ: **Bool**. Výchozí hodnota: **False**.|
|**Povoleno**|Pokud **False**, položka nabídky je zakázána.|
|**Šedý**|Pokud **True**, příkaz nabídky je zpočátku šedě a neaktivní. Typ: **Bool**. Výchozí hodnota: **False**.|
|**Pomoc**|Zarovná položky nabídky na pravé straně. Například **pomáhají** příkazu nabídky je vždy na pravé straně ve všech aplikacích pro Windows. Pokud tuto vlastnost nastavíte na položku nabídky, této položky se zobrazí velmi úplně vpravo a na konci velmi nabídky. Platí pro položky nejvyšší úrovně. Výchozí hodnota: **False**.|
|**ID**|Symbol definovaný v souboru hlaviček. Typ: **Symbol**, **celé číslo**, nebo **řetězec v uvozovkách**. Můžete použít libovolný symbol, který je běžně k dispozici v editorech, i když [okno vlastností](/visualstudio/ide/reference/properties-window) neposkytuje rozevíracího seznamu pro výběr z.|
|**Popup**|Pokud **True**, příkaz nabídky je rozbalovací nabídky. Typ: **Bool**. Výchozí hodnota: **True** pro nejvyšší úrovně nabídky na řádku; jinak nabídek **False**.|
|**řádek**|Obsahuje text, který se zobrazí ve stavovém řádku, když je zvýrazněn tento příkaz. Text je umístěn v tabulce řetězců se stejným identifikátorem příkazu nabídky. Tato vlastnost je k dispozici pro každý typ projektu, ale funkce za běhu je konkrétní knihovny MFC.|
|**Zarovnat zprava doleva.**|Zarovnává doprava příkaz nabídky na řádku nabídek v době běhu. Typ: **Bool**. Výchozí hodnota: **False**.|
|**Right to Left Order**|Umožňuje zobrazovat zprava doleva, pokud rozhraní je lokalizován pro libovolný jazyk, který čte doleva, jako je například hebrejština nebo arabštině příkazů místní nabídky.|
|**Oddělovač**|Pokud **True**, příkaz nabídky je oddělovač. Typ: **Bool**. Výchozí hodnota: **False**.|

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)