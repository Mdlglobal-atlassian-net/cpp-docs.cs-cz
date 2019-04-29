---
title: Chyba kompilátoru C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: ded5a3d459e4b5d1412998aadbaa385864f505a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388858"
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