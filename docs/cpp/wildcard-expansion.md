---
title: "Rozšíření zástupného znaku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _setargv
dev_langs: C++
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2eb1c3861b88db25518753c4f9593cef1fdade92
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wildcard-expansion"></a>Rozšíření zástupného znaku
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).  
  
 Argumenty příkazového řádku jsou zpracovávány rutinu, která je volána **_setargv –** (nebo **_wsetargv** v prostředí široká charakterová), který ve výchozím nastavení nerozšiřuje zástupné znaky do samostatné řetězců v `argv`pole řetězců. Další informace o povolení rozšíření zástupného znaku, najdete v části [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [hlavní: spuštění programu](../cpp/main-program-startup.md)