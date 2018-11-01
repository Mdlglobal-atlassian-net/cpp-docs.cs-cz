---
title: Rozšíření zástupného znaku
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 2d495f94f2e3fb7b88d235edc7b98f8e90775393
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507430"
---
# <a name="wildcard-expansion"></a>Rozšíření zástupného znaku

## <a name="microsoft-specific"></a>Specifické pro Microsoft

K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).

Argumenty příkazového řádku jsou zpracovány rutinou s názvem `_setargv` (nebo `_wsetargv` v prostředí širokých znaků), která standardně Nerozbaluje zástupné znaky do samostatných řetězců v `argv` pole řetězců. Další informace o povolení rozbalování zástupných znaků, najdete [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)