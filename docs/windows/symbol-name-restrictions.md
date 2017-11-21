---
title: "Omezení přístupu názvem symbolů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.restrictions.name
dev_langs: C++
helpviewer_keywords:
- symbol names
- symbols, names
- restrictions, symbol names
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71e50dfa6c35f6f99dc1d7faf3aaf36f3d3a2177
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="symbol-name-restrictions"></a>Omezení názvu symbolu
Omezení pro názvy symbolů jsou následující:  
  
-   Všechny [symboly](../windows/symbols-resource-identifiers.md) musí být jedinečný v rámci oboru aplikace. Tím se zabrání konfliktní definice symbolu v hlavičkových souborů.  
  
-   Platné znaky pro názvu symbolu zahrnout, A-Z,-z, 0 – 9 a podtržítka (_).  
  
-   Názvy symbolů nemůže začínat číslem a jsou omezeny na 247 znaků.  
  
-   Názvy symbolů nesmí obsahovat mezery.  
  
-   Názvy symbolů nejsou velká a malá písmena, ale se zachová, i v případě první definice symbolu. Soubor hlaviček, který definuje symboly se používá k kompilátoru/editoru prostředků a programech C++ označují prostředky, které jsou definované v souboru prostředků. Pro dva názvy symbolů, liší pouze v případě, že, programu C++ zobrazí dvě samostatné symboly při kompilátoru/editoru prostředků se zobrazí oba názvy jako odkazující na jednu jeden symbol.  
  
    > [!NOTE]
    >  Pokud není podle schématu název standardní symbol (ID*_[keyword]) uvedené níže, a název vaší symbol se stane, aby byla stejná jako klíčové slovo ví, že skript kompilátor prostředků, při pokusu o vytvoření souboru skriptu prostředků bude mít za následek zdánlivě náhodné chyby generování, které je obtížné diagnostikovat. Chcete-li tomu zabránit, dodržovat standardní pojmenování schématu.  
  
 Názvy symbolů mít popisný předpon, které označují typ prostředku nebo objekt, které reprezentují. Tyto předpony popisný začínat ID text kombinaci. Microsoft Foundation Class Library (MFC) používá symbol zásady vytváření názvů, které jsou uvedené v následující tabulce.  
  
|Kategorie|Předpona|Použití|  
|--------------|------------|---------|  
|Prostředky|IDR_ IDD_ IDC_ IDI_ IDB_|Accelerator nebo nabídky (a související nebo vlastní prostředky) dialogové okno rastrový obrázek ikony kurzoru|  
|Položky nabídky|ID_|Položky nabídky|  
|Příkazy|ID_|Příkaz|  
|Ovládací prvky a podřízená okna|IDC_|Ovládací prvek|  
|Řetězce|IDS_|Řetězec v tabulce řetězců|  
|MFC|AFX_|Vyhrazeno pro předdefinované symboly MFC|  
  

  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Změna symbolu nebo názvu symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)   
 [Omezení hodnoty symbolu](../windows/symbol-value-restrictions.md)   
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)