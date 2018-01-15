---
title: "Styly seznamů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LBS_STANDARD
- LBS_NODATA
- LBS_OWNERDRAWVARIABLE
- LBS_EXTENDEDSEL
- LBS_USETABSTOPS
- LBS_WANTKEYBOARDINPUT
- LBS_NOTIFY
- LBS_DISABLENOSCROLL
- LBS_HASSTRINGS
- LBS_NOREDRAW
- LBS_NOSEL
- LBS_NOINTEGRALHEIGHT
- LBS_MULTICOLUMN
- LBS_SORT
- LBS_MULTIPLESEL
- LBS_OWNERDRAWFIXED
dev_langs: C++
helpviewer_keywords:
- LBS_NOSEL constant [MFC]
- LBS_NOREDRAW constant [MFC]
- LBS_HASSTRINGS constant [MFC]
- LBS_OWNERDRAWFIXED constant [MFC]
- LBS_WANTKEYBOARDINPUT constant [MFC]
- LBS_STANDARD constant [MFC]
- LBS_MULTIPLESEL constant [MFC]
- LBS_OWNERDRAWVARIABLE constant [MFC]
- LBS_DISABLENOSCROLL constant [MFC]
- LBS_NODATA constant [MFC]
- list boxes [MFC], styles
- LBS_EXTENDEDSEL constant [MFC]
- LBS_MULTICOLUMN constant [MFC]
- LBS_NOTIFY constant [MFC]
- LBS_USETABSTOPS constant [MFC]
- LBS_NOINTEGRALHEIGHT constant [MFC]
- LBS_SORT constant
ms.assetid: 3f357b8d-9118-4f41-9e28-02ed92d1e88f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f52734e26d1965811aded67bc1e1dde6a2c28bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="list-box-styles"></a>Styly seznamů
-   **Lbs_disablenoscroll –** pole se seznamem ukazuje zakázané svislý posuvník při pole se seznamem neobsahuje dostatečný počet položek posun. Bez této styl posuvníku skrytý, pokud seznam neobsahuje dostatečný počet položek.  
  
-   **Lbs_extendedsel –** kterého uživatel může vybrat více položek s použitím klávesu SHIFT a myši nebo speciální kombinace kláves.  
  
-   **Lbs_hasstrings –** určuje pole seznamu vykreslování vlastníka, který obsahuje položky, který se skládá z řetězce. Pole se seznamem udržuje paměti a ukazatele pro řetězce, abyste mohli používat aplikaci `GetText` členské funkce k načtení textu pro danou položku.  
  
-   **Lbs_multicolumn –** určuje více sloupců seznamu, který je vodorovně posunout. `SetColumnWidth` – Členská funkce nastaví šířku sloupců.  
  
-   **Lbs_multiplesel –** přepnuto řetězec výběr pokaždé, když uživatel klikne na tlačítko nebo poklikáním řetězec. Můžete vybrat libovolný počet řetězce.  
  
-   **Lbs_nodata –** určuje pole se seznamem neexistují žádná data. Pokud počet položek v seznamu překročí tisíc, zadejte tento styl. Pole se seznamem bez dat musí mít také **lbs_ownerdrawfixed –** styl, ale nesmí mít **lbs_sort –** nebo **lbs_hasstrings –** stylu.  
  
     Pole se seznamem bez dat vypadá takto: vykreslovaných vlastníkem seznam s tím rozdílem, že neobsahuje žádná data řetězec nebo rastrového obrázku pro položku. Příkazy, které chcete přidat, insert nebo delete položku vždy ignorovat jakékoli zadané položky dat; požadavky a najít si řetězec v rámci pole se seznamem vždy selžou. Odešle systému `WM_DRAWITEM` zpráva do okna vlastníka, když je nutné vykreslit položku. Členové itemID `DRAWITEMSTRUCT` struktura byla dokončena s `WM_DRAWITEM` zprávy určuje číslo řádku položky, které se mají vykreslovat. Pole se seznamem bez dat neodesílá `WM_DELETEITEM` zprávy.  
  
-   **Lbs_nointegralheight –** velikost pole se seznamem je přesně při jeho vytváření pole se seznamem určenou aplikací velikost. Obvykle Windows velikosti pole se seznamem, aby pole se seznamem nezobrazuje částečné položky.  
  
-   **Lbs_noredraw –** pole se seznamem zobrazení není aktualizováno při provedení změn. Tento styl můžete kdykoli změnit odesláním **WM_SETREDRAW** zprávy.  
  
-   **Lbs_nosel –** Určuje, že pole se seznamem obsahuje položky, které můžete zobrazit, ale nejsou vybrány.  
  
-   **Lbs_notify –** nadřazeného okna obdrží zprávu vstupní pokaždé, když uživatel klikne na tlačítko nebo poklikáním na řetězec.  
  
-   **Lbs_ownerdrawfixed –** vlastník pole se seznamem je zodpovědná za kreslení její obsah; položek v seznamu jsou stejné výšku.  
  
-   **Lbs_ownerdrawvariable –** vlastník pole se seznamem je zodpovědná za kreslení její obsah; položek v seznamu jsou proměnné na výšku.  
  
-   **Lbs_sort –** řetězce v seznamu jsou seřazené podle abecedy.  
  
-   **Lbs_standard –** abecedním řetězce v seznamu a nadřazeného okna přijímá zprávy při zadávání pokaždé, když uživatel klikne na tlačítko nebo poklikáním na řetězec. Pole se seznamem obsahuje ohraničení ze všech stran.  
  
-   **Lbs_usetabstops –** umožňuje pole se seznamem rozpoznat a rozbalte karta znaků při kreslení jeho řetězce. Výchozí polohy karty jsou 32 jednotky dialogu. (Jednotky dialogu je vzdálenost vodorovně nebo svisle. Jednu jednotku vodorovné dialogové okno se rovná jeden čtvrtý aktuální základní šířka jednotky dialogu. Základní jednotky dialogu se vypočítávají podle výšky a šířky aktuálním písmem systému. **GetDialogBaseUnits** funkce systému Windows vrátí dialogu aktuální základní jednotky v pixelech.) Tento styl by neměl být použit s **lbs_ownerdrawfixed –**.  
  
-   **Lbs_wantkeyboardinput –** obdrží majitel pole se seznamem `WM_VKEYTOITEM` nebo `WM_CHARTOITEM` zprávy vždy, když uživatel stiskne klávesu při pole se seznamem má vstupu fokus. Umožňuje aplikaci k provedení speciální zpracování na vstupu klávesnice.  
  
## <a name="see-also"></a>Viz také  
 [Styly využívané prostředím MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CListBox::Create](../../mfc/reference/clistbox-class.md#create)   
 [Styly oken seznamu](http://msdn.microsoft.com/library/windows/desktop/bb775149)

