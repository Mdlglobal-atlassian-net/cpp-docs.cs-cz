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
ms.openlocfilehash: 1fdea297bb45a06a08bde4f63f90eabef6ddb539
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857174"
---
# <a name="wildcard-expansion"></a>Rozšíření zástupného znaku

**Specifické pro společnost Microsoft**

K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).

Argumenty příkazového řádku jsou zpracovávány rutinou s názvem `_setargv` (nebo `_wsetargv` v prostředí s velkým znakem), které ve výchozím nastavení nerozšiřují zástupné znaky na samostatné řetězce v poli `argv` řetězců. Další informace o povolení rozšíření zástupných znaků najdete v tématu [rozšiřování argumentů zástupného znaku](../c-language/expanding-wildcard-arguments.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)