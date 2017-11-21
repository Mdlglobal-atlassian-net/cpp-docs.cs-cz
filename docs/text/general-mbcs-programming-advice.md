---
title: "Znakové sady MBCS obecné Rady k programování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 2136f017e177cea80f6832f7c1b9ba4e2d843bcf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="general-mbcs-programming-advice"></a>Obecné rady k programování se znakovou sadou MBCS
Použijte následující tipy:  
  
-   Pro pružnost použijte makra běhu `_tcschr` a `_tcscpy` Pokud je to možné. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Použít běhu C `_getmbcp` funkce a získat informace o aktuální znaková stránka.  
  
-   Nepoužívejte opakovaně řetězcové prostředky. V závislosti na cílový jazyk může mít daný řetězec jiný význam při překladu. Hlavní nabídky "Soubor" na aplikace může například překládat odlišně od řetězec "Soubor" v dialogovém okně. Pokud potřebujete použít více než jeden řetězec se stejným názvem, použijte pro každou jiné ID řetězce.  
  
-   Můžete chtít zjistit, jestli vaše aplikace běží na operačním systému znakovou sadou MBCS. Uděláte to tak, nastavte příznak při spuštění programu; Nespoléhejte na volání rozhraní API.  
  
-   Při navrhování dialogových oken, povolit přibližně 30 % místo navíc je na konci – ovládací prvky pro překlad MBCS statický text.  
  
-   Buďte opatrní při výběru písem pro aplikaci, protože některá písma nejsou dostupné na všech systémech. Například japonské verzi systému Windows 2000 nepodporuje písmo Helvetica.  
  
-   Když vyberete písmo pro dialogová okna, použijte [dialogové okno prostředí MS](http://msdn.microsoft.com/library/windows/desktop/dd374112) místo MS Sans Serif nebo Helvetica. Dialogové okno prostředí MS se nahradí správné písmo v systému před vytvořením dialogové okno. Použití prostředí MS dialogové okno zajišťuje, že všechny změny v operačním systému, jak nakládat s toto písmo bude automaticky k dispozici. (MFC nahradí dialogové okno prostředí MS DEFAULT_GUI_FONT nebo systém písmo v systému Windows 95, Windows 98 a systému Windows NT 4 vzhledem k tomu, že tyto systémy neukládají dialogové okno prostředí MS správně.)  
  
-   Při navrhování vaší aplikace, rozhodněte se, řetězce, které je možné lokalizovat. Pokud máte pochybnosti, předpokládá, že bude lokalizované libovolný daný řetězec. Jako takový nemíchat řetězce, které je možné lokalizovat s těmi, které nelze.  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Inkrementace a dekrementace ukazatelů](../text/incrementing-and-decrementing-pointers.md)