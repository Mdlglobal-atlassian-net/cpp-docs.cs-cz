---
title: Závažná chyba C1126 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3ff02d69679074186e593d5e1c16bdf56d1052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225911"
---
# <a name="fatal-error-c1126"></a>Závažná chyba C1126
"identifikátor": automatické přidělení je větší než velikost  
  
 Místo přidělené pro místní proměnné funkce (a omezené množství místa využitého kompilátoru, jako je například navíc 20 bajtů pro swappable funkce) překračuje limit.  
  
 Chcete-li opravit tuto chybu, použijte `malloc` nebo `new` přidělit velké objemy dat.