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
ms.workload: cplusplus
ms.openlocfilehash: 2c9bbb5dcc706e08b2b985769248969f9bd23201
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="wildcard-expansion"></a>Rozšíření zástupného znaku
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).  
  
 Argumenty příkazového řádku jsou zpracovávány rutinu, která je volána **_setargv –** (nebo **_wsetargv** v prostředí široká charakterová), který ve výchozím nastavení nerozšiřuje zástupné znaky do samostatné řetězců v `argv`pole řetězců. Další informace o povolení rozšíření zástupného znaku, najdete v části [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)