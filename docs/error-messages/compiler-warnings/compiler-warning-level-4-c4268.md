---
title: Upozornění (úroveň 4) C4268 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a8152ef690b9ded63b91b2b6e6f1da6dc2524
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063707"
---
# <a name="compiler-warning-level-4-c4268"></a>Kompilátor upozornění (úroveň 4) C4268

'identifier': 'const' statická/globální data inicializovaná s konstruktorem default generovaným kompilátorem vyplní objekt nulami

A **const** globální nebo statická instance nejsou v netriviálních třídy je inicializován pomocí konstruktoru vygenerovaný kompilátorem výchozí.

## <a name="example"></a>Příklad

```
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Protože je tato instance třídy **const**, hodnota `m_data` nelze změnit.