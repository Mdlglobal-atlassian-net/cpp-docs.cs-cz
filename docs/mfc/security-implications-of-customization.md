---
title: Vliv přizpůsobení na zabezpečení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1416a586af479ea7b476a6c85d45992ba18873ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379415"
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

