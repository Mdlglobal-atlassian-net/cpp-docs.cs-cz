---
title: CXX0039 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8681d73d2889433516b205a47c500193bbeabdb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297765"
---
# <a name="expression-evaluator-error-cxx0039"></a>Chyba při vyhodnocování výrazu CXX0039
symbol je nejednoznačný  
  
 Vyhodnocovací filtr výrazů C nemůže určit, která instance symbol použít ve výrazu. Symbol dojde k více než jednou ve stromu dědičnosti.  
  
 Musíte použít operátor řešení rozsahu (`::`) k explicitnímu zadání instance použít ve výrazu.  
  
 Tato chyba je stejný jako CAN0039.