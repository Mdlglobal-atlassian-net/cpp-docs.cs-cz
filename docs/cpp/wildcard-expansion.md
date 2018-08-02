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
ms.openlocfilehash: 82bb280036bf8ad1886d2943c3ec3e546c2eaff2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466173"
---
# <a name="wildcard-expansion"></a>Rozšíření zástupného znaku
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).  
  
 Argumenty příkazového řádku jsou zpracovány rutinou s názvem `_setargv` (nebo `_wsetargv` v prostředí širokých znaků), která standardně Nerozbaluje zástupné znaky do samostatných řetězců v `argv` pole řetězců. Další informace o povolení rozbalování zástupných znaků, najdete [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [main: spuštění programu](../cpp/main-program-startup.md)