---
title: Pole se seznamem styly | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBS_LOWERCASE
- CBS_SORT
- CBS_OWNERDRAWVARIABLE
- CBS_OEMCONVERT
- CBS_AUTOHSCROLL
- CBS_NOINTEGRALHEIGHT
- CBS_SIMPLE
- CBS_DROPDOWNLIST
- CBS_DROPDOWN
- CBS_UPPERCASE
- CBS_HASSTRINGS
- CBS_DISABLENOSCROLL
- CBS_OWNERDRAWFIXED
dev_langs:
- C++
helpviewer_keywords:
- CBS_OWNERDRAWVARIABLE constant [MFC]
- CBS_NOINTEGRALHEIGHT constant [MFC]
- CBS_SIMPLE constant [MFC]
- CBS_AUTOHSCROLL constant [MFC]
- CBS_OEMCONVERT constant [MFC]
- CBS_DISABLENOSCROLL constant [MFC]
- CBS_HASSTRINGS constant [MFC]
- CBS_LOWERCASE constant [MFC]
- CBS_SORT constant [MFC]
- CBS_DROPDOWN constant [MFC]
- CBS_OWNERDRAWFIXED constant [MFC]
- combo boxes [MFC], styles
- CBS_UPPERCASE constant [MFC]
- CBS_DROPDOWNLIST constant
ms.assetid: d21a5023-e6a2-495b-a6bd-010a515cbc63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ec15f483d9a613e77ad07b6f7f306e84099bced
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="combo-box-styles"></a>Styly polí se seznamem
Následující pole se seznamem styly jsou dostupné v prostředí MFC.  
  
-   **Cbs_autohscroll –** automaticky posune text v textovém poli napravo, když uživatel zadá znak na konci řádku. Pokud tento styl není nastavena, je povolen pouze text, který vyhovuje obdélníková hranici.  
  
-   **Cbs_disablenoscroll –** pole se seznamem ukazuje zakázané svislý posuvník při pole se seznamem neobsahuje dostatečný počet položek posun. Bez této styl posuvníku skrytý, pokud seznam neobsahuje dostatečný počet položek.  
  
-   **Cbs_dropdown –** . podobá se **cbs_simple –**kromě toho, že pole se seznamem se nezobrazí, pokud uživatel vybere ikonu vedle ovládací prvek upravit.  
  
-   **Cbs_dropdownlist –** . podobá se **cbs_dropdown –**kromě toho, že se ovládací prvek upravit nahrazuje položku statický text, který se zobrazuje aktuální výběr v seznamu.  
  
-   **Cbs_hasstrings –** vykreslování vlastníka – pole se seznamem obsahuje položky, který se skládá z řetězce. Pole se seznamem udržuje paměti a ukazatele pro řetězce, abyste mohli používat aplikaci `GetText` členské funkce k načtení textu pro danou položku.  
  
-   **Cbs_lowercase –** převede na malá písmena veškerého textu v poli Výběr a v seznamu.  
  
-   **Cbs_nointegralheight –** Určuje, že velikost pole se seznamem je přesně při jeho vytváření pole se seznamem určenou aplikací velikost. Za normálních okolností Windows velikosti pole se seznamem, aby pole se seznamem nezobrazí dílčí položky.  
  
-   **Cbs_oemconvert –** v ovládacím prvku pole se seznamem úpravy v zadaném textu je převést z znakovou sadu ANSI na znakovou sadu pro výrobce OEM a pak znovu ANSI. To zajistí správnou znak převod při volání `AnsiToOem` funkce systému Windows při převodu řetězce ANSI v poli se seznamem na znaky OEM. Tento styl je vhodný pro seznamem, které obsahují názvy souborů a se vztahuje pouze na pole se seznamem vytvořené pomocí **cbs_simple –** nebo **cbs_dropdown –** stylů.  
  
-   **Cbs_ownerdrawfixed –** vlastník pole se seznamem je zodpovědná za kreslení její obsah; položek v seznamu se stejnou výšku.  
  
-   **Cbs_ownerdrawvariable –** vlastník pole se seznamem je zodpovědná za kreslení její obsah; položek v seznamu jsou proměnné na výšku.  
  
-   **Cbs_simple –** pole se seznamem se zobrazí za všech okolností. Aktuální výběr v seznamu se zobrazí v textovém poli.  
  
-   **Cbs_sort –** automaticky seřadí řetězce zadali do pole se seznamem.  
  
-   **Cbs_uppercase –** převede na velká písmena veškerého textu v poli Výběr a v seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Styly využívané prostředím MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CComboBox::Create] (ccombobox class.md #ccombobox__create   



