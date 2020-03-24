---
title: Upozornění kompilátoru (úroveň 4) C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: 665a21d9f0221b2cf3db111142576669a3b5d728
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198261"
---
# <a name="compiler-warning-level-4-c4626"></a>Upozornění kompilátoru (úroveň 4) C4626

odvozená třída: operátor přiřazení byl implicitně definovaný jako odstraněný, protože operátor přiřazení základní třídy je nedostupný nebo odstraněný.

Operátor přiřazení byl odstraněn nebo není přístupný v základní třídě, a proto nebyl vygenerován pro odvozenou třídu. Jakýkoli pokus o přiřazení objektů tohoto typu způsobí chybu kompilátoru.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4626 a ukazuje, jak ji opravit:

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
