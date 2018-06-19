---
title: Posuny doprava | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2eac057bbf8164915ff645cca098bbbf7c1995a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385774"
---
# <a name="right-shifts"></a>Posuny doprava
Výsledek posunutí doprava záporné hodnoty podepsané integrálních typů  
  
 Posunutí záporné hodnoty doprava dává polovinu absolutní hodnoty zaokrouhlené dolů. Například přihlášeni `short` hodnotu-253 (šestnáctkových 0xFF03, binární 00000011 11111111) zapuštěno správné jeden bit vytváří-127 (šestnáctkových 0xFF81, binární 11111111 10000001). Kladné 253 zapuštěno správné vytváří +126.  
  
 Posuny doprava zachovávají přihlašovací bit podepsaných integrálních typů. Posune-li se celé číslo se znaménkem doprava, zůstane nejvýznamnější bit nastaven. Například, pokud je přihlášeni 0xF0000000 `int`, vytváří 0xF8000000 posunutí doprava. S posunem jako záporné `int` právo 32 časy vytváří 0xFFFFFFFF.  
  
 Posune-li se celé číslo bez znaménka doprava, je nejvýznamnější bit vymazán. Například pokud 0xF000 bez znaménka, výsledkem je 0x7800. Přejdou `unsigned` nebo kladných `int` právo 32 časy vytváří 0x00000000.  
  
## <a name="see-also"></a>Viz také  
 [Celá čísla](../c-language/integers.md)