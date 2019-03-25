---
title: alokátor
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: f9c8de7c8686b89a2ab9570a2558e3f649e545b5
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58417082"
---
# <a name="allocator"></a>alokátor

**Microsoft Specific**

**Alokátoru** Specifikátor deklarace můžete použít pro funkce vlastní přidělení paměti pro zviditelnění přidělení pomocí trasování událostí pro Windows (ETW).

## <a name="syntax"></a>Syntaxe

```
   __declspec(allocator) 
```

## <a name="remarks"></a>Poznámky

Nativní paměť profileru v sadě Visual Studio funguje tak, že shromažďování přidělení data událostí trasování událostí pro Windows, protože ho vygeneroval za běhu. Na úrovni zdroje byly anotované alokátorů CRT a sadu Windows SDK tak, aby jejich přidělení dat se dají zachytit. Pokud vytváříte vlastní alokátory, pak všechny funkce, které vrací ukazatel na nově přidělenou haldě paměť může být doplněny pomocí `__declspec(allocator)`, jak je znázorněno v následujícím příkladu myMalloc:

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Další informace najdete v tématu [měření využití paměti v aplikaci Visual Studio](/visualstudio/profiling/memory-usage) a [vlastní nativní události haldy trasování událostí pro Windows](/visualstudio/profiling/custom-native-etw-heap-events).