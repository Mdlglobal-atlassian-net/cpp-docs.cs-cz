---
title: alokátor
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 2e2615829f6491bf660859fbc86ebcd07a56c5fe
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857681"
---
# <a name="allocator"></a>alokátor

**Specifické pro společnost Microsoft**

Specifikátor deklarace **přidělujícího modulu** lze použít pro vlastní funkce přidělování paměti, aby bylo možné alokace zviditelnit prostřednictvím trasování událostí pro Windows (ETW).

## <a name="syntax"></a>Syntaxe

```
   __declspec(allocator) 
```

## <a name="remarks"></a>Poznámky

Nativní profil paměti v sadě Visual Studio funguje tak, že shromažďuje data události trasování událostí pro Windows vygenerovaná během běhu. Na úrovni zdroje byly anotované alokátorů CRT a sadu Windows SDK tak, aby jejich přidělení dat se dají zachytit. Pokud píšete vlastní přidělování, pak všechny funkce, které vracejí ukazatel na nově přidělenou paměť haldy, mohou být upraveny pomocí `__declspec(allocator)`, jak je vidět v tomto příkladu pro myMalloc:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Další informace najdete v tématu [měření využití paměti v aplikaci Visual Studio](/visualstudio/profiling/memory-usage) a [vlastní nativní události haldy ETW](/visualstudio/profiling/custom-native-etw-heap-events).

**Specifické pro konec Microsoftu**
