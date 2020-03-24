---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 6d9429aa7c079f0f99a936019e5945092dc1f006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181522"
---
# <a name="allocate"></a>allocate

**Specifické pro společnost Microsoft**

Specifikátor deklarace **allocate** pojmenovává datový segment, ve kterém bude datová položka přidělena.

## <a name="syntax"></a>Syntaxe

```
   __declspec(allocate("segname")) declarator
```

## <a name="remarks"></a>Poznámky

Název *segname* musí být deklarován pomocí jedné z následujících direktiv pragma:

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [section](../preprocessor/section.md)

## <a name="example"></a>Příklad

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
