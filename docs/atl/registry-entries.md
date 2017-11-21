---
title: "Položky registru (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 013a5827af630e8190e622940c1fd3872a46a5d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="registry-entries"></a>Položky registru
Model DCOM zaveden koncept ID aplikace (AppIDs), které skupiny možností konfigurace pro jeden nebo více objektů DCOM v centrálním umístění v registru. AppID zadáte tak, že zadáte její hodnota v AppID s názvem hodnotu CLSID objektu.  
  
 Ve výchozím nastavení používá služby generované ATL jeho CLSID jako identifikátor GUID pro jeho ID aplikace. V části `HKEY_CLASSES_ROOT\AppID`, můžete zadat položky specifické pro model DCOM. Na začátku existují dvě položky:  
  
-   `LocalService`, s hodnotou stejný jako název služby. Existuje-li tato hodnota, použije se místo `LocalServer32` klíče v části identifikátor CLSID.  
  
-   `ServiceParameters`, s hodnotou rovna `-Service`. Tato hodnota určuje parametry, které budou předány služby při jeho spuštění. Všimněte si, že tyto parametry jsou předány služby `ServiceMain` fungovat, není `WinMain`.  
  
 Všechny služby DCOM také musí vytvořit jiný klíč `HKEY_CLASSES_ROOT\AppID`. Tento klíč je stejný jako název souboru EXE se a funguje jako křížových odkazů, protože obsahuje hodnotu AppID přejdete zpět na AppID položky.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)

