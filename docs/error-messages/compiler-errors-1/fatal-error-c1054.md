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
ms.workload: cplusplus
ms.openlocfilehash: c39ba89a36791c56c0b71637cac388b28dc372f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1054"></a>Závažná chyba C1054
omezení kompilátoru: Inicializátory vnořeny příliš hluboko  
  
 Kód překračuje limit vnoření na inicializátory (v závislosti na kombinaci typů během inicializace úrovně 10 až 15).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Datové typy během inicializace ke snížení vnoření zjednodušte.  
  
2.  Inicializace proměnných v samostatných příkazů po deklaraci.