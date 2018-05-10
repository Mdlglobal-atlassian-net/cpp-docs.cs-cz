---
title: Znakové sady MBCS obecné Rady k programování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab2b67c82a04a0c355761ec6572a9718d03c4666
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="general-mbcs-programming-advice"></a>Obecné rady k programování se znakovou sadou MBCS
Použijte následující tipy:  
  
-   Pro pružnost použijte makra běhu `_tcschr` a `_tcscpy` Pokud je to možné. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Použít běhu C `_getmbcp` funkce a získat informace o aktuální znaková stránka.  
  
-   Nepoužívejte opakovaně řetězcové prostředky. V závislosti na cílový jazyk může mít daný řetězec jiný význam při překladu. Hlavní nabídky "Soubor" na aplikace může například překládat odlišně od řetězec "Soubor" v dialogovém okně. Pokud potřebujete použít více než jeden řetězec se stejným názvem, použijte pro každou jiné ID řetězce.  
  
-   Můžete chtít zjistit, jestli vaše aplikace běží na operačním systému znakovou sadou MBCS. Uděláte to tak, nastavte příznak při spuštění programu; Nespoléhejte na volání rozhraní API.  
  
-   Při navrhování dialogových oken, povolit přibližně 30 % místo navíc je na konci – ovládací prvky pro překlad MBCS statický text.  
  
-   Buďte opatrní při výběru písem pro aplikaci, protože některá písma nejsou dostupné na všech systémech.  
  
-   Když vyberete písmo pro dialogová okna, použijte [dialogové okno prostředí MS](http://msdn.microsoft.com/library/windows/desktop/dd374112) místo MS Sans Serif nebo Helvetica. Dialogové okno prostředí MS se nahradí správné písmo v systému před vytvořením dialogové okno. Použití prostředí MS dialogové okno zajišťuje, že všechny změny v operačním systému, jak nakládat s toto písmo bude automaticky k dispozici. (MFC nahradí dialogové okno prostředí MS DEFAULT_GUI_FONT nebo systém písmo v systému Windows 95, Windows 98 a systému Windows NT 4 vzhledem k tomu, že tyto systémy neukládají dialogové okno prostředí MS správně.)  
  
-   Při navrhování vaší aplikace, rozhodněte se, řetězce, které je možné lokalizovat. Pokud máte pochybnosti, předpokládá, že bude lokalizované libovolný daný řetězec. Jako takový nemíchat řetězce, které je možné lokalizovat s těmi, které nelze.  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Inkrementace a dekrementace ukazatelů](../text/incrementing-and-decrementing-pointers.md)