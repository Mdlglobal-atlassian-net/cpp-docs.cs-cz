---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: 38346e41c1e943e9bfda70668a163c630a0b9599
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178870"
---
# <a name="selectany"></a>selectany

**Specifické pro společnost Microsoft**

Říká kompilátoru, že deklarovaná položka globálních dat (proměnná nebo objekt) je vybrána libovolnou sekvencí COMDAT (zabalenou funkcí).

## <a name="syntax"></a>Syntaxe

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Poznámky

Pokud je v době spojení nalezeno více definic sekvencí COMDAT, linker jednu vybere a zbytek zahodí. Pokud je vybrána možnost linkeru [/OPT: ref](../build/reference/opt-optimizations.md) (optimalizace), pak dojde k odstranění všech neodkazovaných datových položek ve výstupu linkeru COMDAT eliminace.

Konstruktory a přiřazení pomocí globálních funkcí nebo statických metod v deklaraci nevytvoří odkaz a nezabrání eliminaci možnosti /OPT:REF. Vedlejší účinky takového kódu by neměly být závislé na tom, zda neexistují žádné odkazy na tato data.

Pro dynamicky inicializované globální objekty **selectany** zruší inicializační kód neodkazovaného objektu.

V projektu EXE nebo DLL lze položku globálních dat obvykle inicializovat pouze jednou. **selectany** lze použít při inicializaci globálních dat definovaných záhlavími, pokud se stejná hlavička zobrazuje ve více než jednom zdrojovém souboru. **selectany** je k dispozici jak v C C++ , tak v kompilátorech.

> [!NOTE]
>  **selectany** lze použít pouze na skutečnou inicializaci globálních datových položek, které jsou externě viditelné.

## <a name="example"></a>Příklad

Tento kód ukazuje, jak použít atribut **selectany** :

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>Příklad

Tento kód ukazuje, jak použít atribut **selectany** k zajištění skládání dat COMDAT při použití možnosti linkeru [/OPT: ICF](../build/reference/opt-optimizations.md) . Všimněte si, že data musí být označena pomocí **selectany** a umístěna do oddílu **const** (ReadOnly). Část jen pro čtení je nutné explicitně zadat.

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
