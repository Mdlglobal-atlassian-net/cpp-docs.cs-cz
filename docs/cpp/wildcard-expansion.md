---
title: Rozšíření zástupného znaku | Microsoft Docs
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
ms.openlocfilehash: bb58d5da479d686cac0d18c9d36e500bd6b5a632
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420643"
---
# <a name="wildcard-expansion"></a>Rozšíření zástupného znaku
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).  
  
 Argumenty příkazového řádku jsou zpracovávány rutinu, která je volána **_setargv –** (nebo **_wsetargv** v prostředí široká charakterová), který ve výchozím nastavení nerozšiřuje zástupné znaky do samostatné řetězců v `argv`pole řetězců. Další informace o povolení rozšíření zástupného znaku, najdete v části [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)