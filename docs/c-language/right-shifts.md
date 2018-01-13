---
title: Posuny doprava | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 307cf91bf86f2912ad6cafa7e89f48e614c3865a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="right-shifts"></a>Posuny doprava
Výsledek posunutí doprava záporné hodnoty podepsané integrálních typů  
  
 Posunutí záporné hodnoty doprava dává polovinu absolutní hodnoty zaokrouhlené dolů. Například přihlášeni `short` hodnotu-253 (šestnáctkových 0xFF03, binární 00000011 11111111) zapuštěno správné jeden bit vytváří-127 (šestnáctkových 0xFF81, binární 11111111 10000001). Kladné 253 zapuštěno správné vytváří +126.  
  
 Posuny doprava zachovávají přihlašovací bit podepsaných integrálních typů. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Například, pokud je přihlášeni 0xF0000000 `int`, vytváří 0xF8000000 posunutí doprava. S posunem jako záporné `int` právo 32 časy vytváří 0xFFFFFFFF.  
  
 Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán. Například pokud 0xF000 bez znaménka, výsledkem je 0x7800. Přejdou `unsigned` nebo kladných `int` právo 32 časy vytváří 0x00000000.  
  
## <a name="see-also"></a>Viz také  
 [Celá čísla](../c-language/integers.md)