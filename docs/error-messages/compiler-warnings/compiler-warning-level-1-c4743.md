---
title: Kompilátor upozornění (úroveň 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: 53ead0e34b55eca44399cee09f1947a12e1eadd3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611827"
---
# <a name="compiler-warning-level-1-c4743"></a>Kompilátor upozornění (úroveň 1) C4743

"*typ*"má jinou velikost v"*file1*"a"*file2*': *číslo* a *číslo* bajtů

Externí proměnné odkazovat nebo definované ve dvou souborech má různé typy v těchto souborech a kompilátor určili, že velikost proměnné v *file1* se liší od velikost proměnné v *file2*.

## <a name="remarks"></a>Poznámky

Je důležité případu při toto upozornění může být generována pro C++. Pokud deklarujete stejné typy se stejným názvem ve dvou různých souborech, pokud tyto deklarace obsahovat virtuální funkce, a pokud deklarace nejsou stejné, kompilátor může vygenerovat upozornění C4744 pro tabulky virtuálních funkcí. Upozornění dochází, protože existují dvě tabulky různé velikosti virtuálních funkcí pro stejného typu a linkeru musíte zvolit jeden z nich začlenit do spustitelného souboru.  Je možné, že může způsobit ve svém programu volání nesprávné virtuální funkce.

Pokud chcete vyřešit toto upozornění, použijte stejné definice typu nebo používat jiné názvy typů nebo proměnné.

## <a name="example"></a>Příklad

Následující ukázka generuje C4743. Chcete-li zkompilovat ji, oba soubory umístit do stejné složky a potom spusťte  

```cmd
cl /EHsc /W1 /GL /O2 C4743a.cpp C4743b.cpp
```

```cpp
// C4743a.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

```cpp
// C4743b.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```
