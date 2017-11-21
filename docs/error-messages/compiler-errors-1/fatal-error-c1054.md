---
title: "Závažná chyba C1054 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1054
dev_langs: C++
helpviewer_keywords: C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d02d8eb05633d7250dc3f7ee85dd78ccf4153052
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1054"></a>Závažná chyba C1054
omezení kompilátoru: Inicializátory vnořeny příliš hluboko  
  
 Kód překračuje limit vnoření na inicializátory (v závislosti na kombinaci typů během inicializace úrovně 10 až 15).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Datové typy během inicializace ke snížení vnoření zjednodušte.  
  
2.  Inicializace proměnných v samostatných příkazů po deklaraci.