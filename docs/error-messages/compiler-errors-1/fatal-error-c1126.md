---
title: "Závažná chyba C1126 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1126
dev_langs: C++
helpviewer_keywords: C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f5346a3adb5535242207ebc3a3c9b2fcffa7a40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1126"></a>Závažná chyba C1126
"identifikátor": automatické přidělení je větší než velikost  
  
 Místo přidělené pro místní proměnné funkce (a omezené množství místa využitého kompilátoru, jako je například navíc 20 bajtů pro swappable funkce) překračuje limit.  
  
 Chcete-li opravit tuto chybu, použijte `malloc` nebo `new` přidělit velké objemy dat.