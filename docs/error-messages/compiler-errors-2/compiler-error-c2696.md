---
title: Chyba kompilátoru C2696 | Dokumentace Microsoftu
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
ms.openlocfilehash: e6e76b0c11d329c734b0609c540aca4315c7ed9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108739"
---
# <a name="compiler-error-c2696"></a>Chyba kompilátoru C2696

Nelze vytvořit dočasný objekt spravovaného typu 'type'

Odkazy na `const` v nespravované aplikaci způsobit, že kompilátor volání konstruktoru a vytvořit dočasný objekt v zásobníku. Ale spravovanou třídu nikdy se dají vytvořit na zásobníku.

C2696 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**.
