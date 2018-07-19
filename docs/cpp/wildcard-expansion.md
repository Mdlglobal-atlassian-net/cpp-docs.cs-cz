---
title: Rozšíření zástupného znaku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4de54cbbe978534a42dcb9cbfa677eb1597aa5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939133"
---
# <a name="wildcard-expansion"></a>Rozšíření zástupného znaku
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).  
  
 Argumenty příkazového řádku jsou zpracovány rutinou s názvem `_setargv` (nebo `_wsetargv` v prostředí širokých znaků), která standardně Nerozbaluje zástupné znaky do samostatných řetězců v `argv` pole řetězců. Další informace o povolení rozbalování zástupných znaků, najdete [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)