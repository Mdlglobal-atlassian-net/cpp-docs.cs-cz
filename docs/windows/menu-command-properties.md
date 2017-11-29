---
title: "Vlastnosti příkazu nabídky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: menu items, properties
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 463db89257623d9464bb1e562261362ecf1dc68c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="menu-command-properties"></a>Vlastnosti příkazu nabídky
Níže uvedené informace jsou uspořádána podle vlastnosti nabídky, které se zobrazují v [vlastnosti – okno](/visualstudio/ide/reference/properties-window) když vyberete příkaz nabídky. Tyto podmínky jsou uvedeny abecedně Přestože okno vlastností můžete také zobrazit tyto vlastnosti podle kategorie.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Rozdělit**|Může být jedna z těchto hodnot:<br /><br /> -   **Žádný** (výchozí): žádná zalomení.<br />-   **Sloupec**: pro statické nabídky, tato hodnota umístí příkaz nabídky na nový řádek. Tato hodnota pro místní nabídky, umístí příkaz nabídky nový sloupec s žádné hranici mezi sloupce. Nastavení této vlastnosti ovlivní vzhled nabídky pouze za běhu, není v editoru nabídky.<br />-   **Panel**: je stejné jako sloupec, pouze pro místní nabídky, nový sloupec tuto hodnotu odděluje od původního sloupec s svislá čára. Nastavení této vlastnosti ovlivní vzhled nabídky pouze za běhu, není v editoru nabídky.|  
|**Popisek**|Text, který označuje příkaz nabídky (název nabídky). Chcete-li jedno z písmen v záhlaví nabídky příkaz klávesovými klíč, předcházet ampersand (&).|  
|**Zaškrtnutí**|V případě hodnoty True je původně zaškrtnutí příkazu nabídky. Typ: Bool. Výchozí: False.|  
|**Povoleno**|Pokud **False**, položky nabídky je zakázána.|  
|**Šedý**|V případě hodnoty True je příkaz nabídky původně šedým a neaktivní. Typ: Bool. Výchozí: False.|  
|**Pomoc**|Zarovnává položku nabídky vpravo. Například **pomoci** příkazu nabídky je vždy na pravé straně v všechny aplikace systému Windows. Pokud tuto vlastnost nastavte u položky nabídky, že položka se zobrazí na velmi pravém a na konci velmi v nabídce. Platí pro položky nejvyšší úrovně. Výchozí hodnota: **False**.|  
|**ID**|Symbol definované v záhlaví souboru. Typ: Symbol, celé číslo nebo řetězec v uvozovkách. Můžete použít všechny symbol, který je běžně k dispozici v žádném z editory, i když [vlastnosti – okno](/visualstudio/ide/reference/properties-window) neposkytuje rozevíracího seznamu můžete vybrat z.|  
|**Místní nabídka**|V případě hodnoty True je příkaz nabídky místní nabídky. Typ: Bool. Výchozí hodnota: True nabídek nejvyšší úrovně v řádku nabídek; jinak hodnota False.|  
|**Výzva**|Obsahuje text, který se zobrazí ve stavovém řádku, když je označený tento příkaz nabídky. Text je umístěn v tabulce řetězců se stejným identifikátorem jako příkaz nabídky. Tato vlastnost je k dispozici pro jakýkoli typ projektu, ale je běhové funkce MFC konkrétní.|  
|**Justify zprava doleva**|Zarovná příkaz nabídky v řádku nabídek v době běhu vpravo. Typ: Bool. Výchozí: False.|  
|**Právo na levém pořadí**|Umožňuje zobrazit zprava doleva při rozhraní je lokalizace do jakýkoli jazyk, který čte doleva, jako je například hebrejština nebo arabské příkazů nabídky.|  
|**Oddělovač**|V případě hodnoty True je příkaz nabídky oddělovač. Typ: Bool. Výchozí: False.|  
  

  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor nabídek](../windows/menu-editor.md)