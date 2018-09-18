---
title: Upozornění (úroveň 4) C4626 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4626
dev_langs:
- C++
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16ae3e9d9e54d54a419bfde2250fc02f780e8e54
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083658"
---
# <a name="compiler-warning-level-4-c4626"></a>Kompilátor upozornění (úroveň 4) C4626

'derived class': operátor přiřazení je implicitně definovaný jako odstranit, protože operátor přiřazení základní třídy je nedostupné nebo odstraněné

Operátor přiřazení se odstranil nebo není k dispozici v základní třídě a proto se nevygeneroval pro odvozenou třídu. Jakýkoliv pokus o přiřazení objekty tohoto typu způsobí chybu kompilátoru.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4626 a ukazuje, jak ho opravit:

```
// C4626
// compile with: /W4
#pragma warning(default : 4626)
class B
{
// public:
   B& operator = (const B&)
   {
      return *this;
   }
};

class D : public B
{

}; // C4626 - to fix, make B's copy constructor public

int main()
{
   D m;
   D n;
   // m = n;   // this line will cause an error
}
```