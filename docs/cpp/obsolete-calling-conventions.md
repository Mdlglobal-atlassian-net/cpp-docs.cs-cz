---
title: Zastaralé konvence volání | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs:
- C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d2a6188cf9d8c8283a6c03a2ca6c701e28baf0d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32419843"
---
# <a name="obsolete-calling-conventions"></a>Zastaralé konvence volání
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 **__Pascal**, **__fortran**, a **__syscall** konvence volání již nejsou podporovány. Jejich funkce lze simulovat pomocí jedné z podporovaných konvencí volání a vhodné možnosti linkeru.  
  
 \<odkazující na Windows > teď podporuje **WINAPI** makro, což znamená, že je k příslušné konvence volání pro cíl. Použití **WINAPI** kde dřív používal **PASCAL** nebo **__far \__pascal**.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)