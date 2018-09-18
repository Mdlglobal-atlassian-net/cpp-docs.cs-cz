---
title: Prázdné znaky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- white space, characters
- characters, white space
ms.assetid: 030ccbdc-2db3-4dd0-88c8-f5c2669ddebf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3aa487ee277954470cdd8b16f9f64f465c195897
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055686"
---
# <a name="white-space-characters"></a>Prázdné znaky

Znaky mezery, tabulátoru, odřádkování, konce řádku, formfeed, svislého tabulátoru a nového řádku jsou nazývány „prázdné znaky“, protože slouží stejnému účelu jako mezery mezi slovy a řádky v tištěném textu — usnadňují čtení. Tokeny jsou odděleny (ohraničeny) prázdnými znaky a jinými tokeny, například operátory a interpunkcí. Při analýze kódu kompilátor jazyka C ignoruje prázdné znaky, nejsou-li použity jako oddělovače nebo komponenty znakových konstant nebo textových literálů. Použitím prázdných znaků lze program zpřehlednit. Kompilátor zpracovává jako prázdné znaky i komentáře.

## <a name="see-also"></a>Viz také

[Tokeny jazyka C](../c-language/c-tokens.md)