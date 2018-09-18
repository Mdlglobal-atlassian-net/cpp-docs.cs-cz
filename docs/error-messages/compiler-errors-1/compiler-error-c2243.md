---
title: Chyba kompilátoru C2243 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef5d3a6c20ff147ac2a4b765c7779cec9f19627e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102226"
---
# <a name="compiler-error-c2243"></a>Chyba kompilátoru C2243

"typ převodu: převod z 'type1' na 'type2' existuje, ale je nedostupný

Přístup k ochraně (`protected` nebo `private`) nemůže převod z ukazatele na odvozenou třídu na ukazatel na základní třídu.

Následující ukázka generuje C2243:

```
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

Základní třídy s `protected` nebo `private` přístupu nejsou dostupné pro klienty odvozené třídy. Tyto úrovně řízení přístupu slouží k označení, že je základní třídy, která by měla být viditelná klientům podrobnosti implementace. Použijte veřejnou odvození, pokud mají klienti mají přístup k implicitní převod ukazatele na odvozenou třídu na ukazatel na základní třídu odvozené třídy.