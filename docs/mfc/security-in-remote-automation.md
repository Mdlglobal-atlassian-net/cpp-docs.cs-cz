---
title: "Zabezpečení vzdálené automatizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AllowRemoteActivation [MFC]
- Remote Automation [MFC], security
- activating objects [MFC]
- security [MFC]
- Automation objects [MFC], security options
- object activation [MFC]
- security [MFC], Remote Automation
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a7ad2d09d45747733bd79fd6fe2a7139cef5269a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="security-in-remote-automation"></a>Zabezpečení vzdálené automatizace
Vzdálená automatizace podporuje základní úroveň zabezpečení umožňující zapisovač aplikace serveru (nebo místo toho správce) k určení, jak může vzdáleně aktivovat určitý objekt. Všechny objekty automatizace na daný systém může být globálně nastaven na "Zakázat Vzdálená aktivace" nebo "povolit vzdálená aktivace". Kromě a více často jednotlivé objekty může mít například tyto funkce. Vzdálená automatizace používá klíč v nastavení registru pro každý objekt, **AllowRemoteActivation**určete, zda daný server mohou být aktivovány vzdáleně. Pokud tento režim používejte systémové nastavení, pak každý objekt v registru může být přiřazen tento klíč a jednotlivých stav každé z nich může být nastaven na "Ano" nebo "Ne" podle potřeby.  
  
 Pokud serveru systému Windows NT nebo Windows 2000, je alternativní forma zabezpečení povoleno. V tomto případě Vzdálená automatizace používá NT seznam řízení přístupu (ACL) k určení, které uživatele nebo skupiny nebo skupiny uživatelů, může vzdáleně aktivaci daného serveru.  
  
 Všimněte si, že možnosti zabezpečení platí pro celý objekt; není možné nastavit atributy určité rozhraní, nebo jednotlivé vlastnosti nebo metody na tento objekt.  
  
 Pomocí připojení vzdálené automatizace (RAC) Správce může být nastaven všechny možnosti zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálená automatizace](../mfc/remote-automation.md)

