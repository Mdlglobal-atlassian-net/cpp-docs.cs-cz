---
title: "Prázdné znaky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- white space, characters
- characters, white space
ms.assetid: 030ccbdc-2db3-4dd0-88c8-f5c2669ddebf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51476c05774103ed439ae45888717378e9f59fac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="white-space-characters"></a>Prázdné znaky
Znaky mezery, tabulátoru, odřádkování, konce řádku, formfeed, svislého tabulátoru a nového řádku jsou nazývány „prázdné znaky“, protože slouží stejnému účelu jako mezery mezi slovy a řádky v tištěném textu — usnadňují čtení. Tokeny jsou odděleny (ohraničeny) prázdnými znaky a jinými tokeny, například operátory a interpunkcí. Při analýze kódu kompilátor jazyka C ignoruje prázdné znaky, nejsou-li použity jako oddělovače nebo komponenty znakových konstant nebo textových literálů. Použitím prázdných znaků lze program zpřehlednit. Kompilátor zpracovává jako prázdné znaky i komentáře.  
  
## <a name="see-also"></a>Viz také  
 [Tokeny jazyka C](../c-language/c-tokens.md)