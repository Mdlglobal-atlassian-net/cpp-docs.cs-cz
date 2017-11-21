---
title: "Vliv přizpůsobení na zabezpečení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 20cdc74d68f927d03df6c2945cfe184c4708bc6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="security-implications-of-customization"></a>Vliv přizpůsobení na zabezpečení
Toto téma popisuje potenciální slabá místa zabezpečení v prostředí MFC.  
  
## <a name="potential-security-weakness"></a>Potenciální slabá místa zabezpečení  
 MFC umožňuje uživateli upravit vzhled uživatelské rozhraní aplikace, například vzhled tlačítek a ikon. MFC podporuje i uživatelem definované nástroje, které umožňují uživateli provést příkazy prostředí. Chyba zabezpečení nastane, protože vlastní nastavení aplikace jsou uloženy v profilu uživatele v registru. Každý, kdo může získat přístup k registru můžete upravit tato nastavení a změnit aplikace vzhled a chování. Například může správce v počítači zosobnění uživatele tak, že uživatele aplikace provést libovolné programy (i ze síťové sdílené složky).  
  
## <a name="workarounds"></a>Alternativní řešení  
 Doporučujeme, abyste tyto tři způsoby zavřete slabá místa zabezpečení v registru:  
  
-   Šifrovat data, která je uložená existuje  
  
-   Uložení dat v zabezpečené souboru místo v registru.  
  
     Aby bylo možné tyto první dva způsoby, odvození třídy z [CSettingsStore třída](../mfc/reference/csettingsstore-class.md) a přepsat její metody k implementaci šifrování nebo úložiště mimo registru.  
  
-   Přizpůsobení lze zakázat i ve vaší aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md)

