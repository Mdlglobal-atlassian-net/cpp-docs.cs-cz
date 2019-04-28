---
title: Kompilátor upozornění (úroveň 4) C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: cb00365d12a60885a86a42417bf1c1052a5c6d6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349601"
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