---
title: Koprocesor plovoucí desetinné čárky a konvence volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66ccd54c4abb1d8d9761d5ded88beba76bfae043
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401351"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor plovoucí desetinné čárky a konvence volání
Při psaní sestavení koprocesor pro plovoucí rutiny, musíte zachovat plovoucí bodu řídicí slovo a vyčistit zásobník koprocesoru, pokud se vrátí **float** nebo **double** hodnotu (která funkce by měla vrátit v ST(0)).  
  
## <a name="see-also"></a>Viz také:  
 [Konvence volání](../cpp/calling-conventions.md)