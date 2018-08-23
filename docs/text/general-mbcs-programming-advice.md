---
title: Rady k programování se znakovou sadu MBCS obecné | Dokumentace Microsoftu
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a23ed1283241d3582c0bd548553cb2fed9a47fa
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596792"
---
# <a name="general-mbcs-programming-advice"></a>Obecné rady k programování se znakovou sadou MBCS
Použijte následující tipy:  
  
-   Zajišťuje tak flexibilitu, použijte makra za běhu `_tcschr` a `_tcscpy` Pokud je to možné. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Použití za běhu C `_getmbcp` funkce získáte informace o aktuální znakové stránce.  
  
-   Nepoužívejte opakovaně řetězcové prostředky. V závislosti na cílový jazyk daný řetězec může mít jiný význam při překladu. Hlavní nabídky "Soubor" na aplikace může například překládat odlišně od řetězcem "File" v dialogovém okně. Pokud potřebujete použít více než jeden řetězec se stejným názvem, použijte jiný řetězec ID pro každý.  
  
-   Můžete chtít zjistit, jestli vaše aplikace běží v operačním systému povolena znakové sady MBCS. Uděláte to tak, nastavte příznak, který při spuštění programu; Nespoléhejte na volání rozhraní API.  
  
-   Při navrhování dialogových oknech, povolte přibližně 30 % mezery na konci ovládacích prvků statického textu pro překlad znakové sady MBCS.  
  
-   Buďte opatrní při výběru písma pro vaši aplikaci, protože se některá písma nejsou k dispozici na všech systémech.  
  
-   Při výběru písma pro dialogová okna, použijte [MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112) místo Serif MS sítě SAN nebo Helvetica. Před vytvořením dialogové okno se nahradí MS Shell Dlg s použitím správného písma v systému. Použití MS Shell Dlg zajistí, že všechny změny v operačním systému se toto písmo budou automaticky dostupné. (MFC nahradí MS Shell Dlg DEFAULT_GUI_FONT nebo systémové písmo na Windows 95, Windows 98 a Windows NT 4 vzhledem k tomu, že tyto systémy nezpracuje MS Shell Dlg správně.)  
  
-   Při návrhu aplikace, rozhodněte, které řetězce může být lokalizována. Pokud máte pochybnosti, se předpokládá, že bude lokalizovaný libovolný daný řetězec. V důsledku toho Nekombinujte řetězce, které může být lokalizována s těmi, které nelze.  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Inkrementace a dekrementace ukazatelů](../text/incrementing-and-decrementing-pointers.md)