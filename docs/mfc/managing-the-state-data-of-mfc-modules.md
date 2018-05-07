---
title: Správa údajů o stavu modulů knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d87b2a601e6e25d61de6ca6ad639ac6a62861ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Správa údajů o stavu modulů knihovny MFC
Tento článek popisuje data o stavu modulů knihovny MFC a jak se tento stav bude aktualizován, jakmile tok provádění (kód cesta provede aplikace při provádění) zadá a zanechá modul. Stavy modulů s přepínání `AFX_MANAGE_STATE` a `METHOD_PROLOGUE` makra je také popsáno.  
  
> [!NOTE]
>  Termín "modul" zde odkazuje spustitelný program, nebo knihovna DLL (nebo sadu knihoven DLL), pracovat nezávisle na zbytek aplikace, ale používá sdílené kopie knihovny MFC DLL. Ovládací prvek ActiveX je typický příklad modulu.  
  
 Jak je znázorněno na následujícím obrázku, má MFC data o stavu pro každý modul používaný v aplikaci. Mezi tato data patří například popisovače instance systému Windows (používané pro načítání prostředků), odkazy na aktuální `CWinApp` a `CWinThread` objekty aplikace, počty odkaz na modul OLE a celou řadu mapy, které udržují připojení mezi Windows objekt obslužné rutiny a odpovídajících instancí objektů MFC. Ale pokud aplikace používá více modulů, data o stavu každého modulu není aplikace široké. Místo toho každý modul má svou vlastní privátní kopii dat o stavu MFC.  
  
 ![Stav dat jeden modul &#40;aplikace&#41;](../mfc/media/vc387n1.gif "vc387n1")  
Údajů o stavu jeden modul (aplikace)  
  
 Data o stavu modul je obsažen ve struktuře a je vždy k dispozici prostřednictvím ukazatel na této struktury. Tok provádění zadá konkrétního modulu, jak je znázorněno na následujícím obrázku, musí být stav tohoto modulu stavu "aktuální" nebo "efektivní". Každý objekt vlákno proto má ukazatel na strukturu efektivní stav této aplikace. Zachování tento ukazatel aktualizován na všech časy je důležité pro globální stav aplikace pro správu a údržbu integritu každý modul stavu. Nesprávný správu globální stav může způsobit nepředvídatelné chování aplikací.  
  
 ![Stav dat více modulů](../mfc/media/vc387n2.gif "vc387n2")  
Údajů o stavu více modulů  
  
 Jinými slovy každý modul je zodpovědná za správně přepínání mezi stavy modulů všechny jeho vstupní body. "Vstupní bod" je jakékoli místo, kde tok provádění můžete zadat kód modulu. Vstupní body patří:  
  
-   [Exportované funkce v knihovně DLL](../mfc/exported-dll-function-entry-points.md)  
  
-   [Členské funkce COM – rozhraní](../mfc/com-interface-entry-points.md)  
  
-   [Procedury oken](../mfc/window-procedure-entry-points.md)  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

