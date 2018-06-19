---
title: C2696 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2696
dev_langs:
- C++
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65ccdd6d2c8c34c360811b80d5a93abe76f5ef8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235036"
---
# <a name="compiler-error-c2696"></a>C2696 chyby kompilátoru
Nelze vytvořit dočasný objekt spravovaného typu "typ"  
  
Odkazuje na `const` v nespravované program způsobit kompilátoru volání konstruktoru a vytvořit dočasný objekt v zásobníku. V zásobníku však lze nikdy vytvořit spravovanou třídou.  
  
C2696 je dostupný, pomocí možnosti zastaralé kompilátoru pouze **/clr:oldSyntax**.  
