---
title: noreturn | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133fc70c5c2b8bb8f794746c1d5ca11be97b817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031038"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Specifické pro Microsoft

To **__declspec** atribut oznamuje kompilátoru, že funkce nevrací. V důsledku toho kompilátor ví, že kód následující za voláním **__declspec(noreturn)** funkce nedostupný.

Pokud kompilátor najde funkci s cestou řízení, která nevrací hodnotu, vygeneruje upozornění (C4715) nebo chybovou zprávu (C2202). Pokud cesta správy není dostupný kvůli funkci, která se nikdy nevrátí, můžete použít **__declspec(noreturn)** zabránit tohoto varování nebo chyby.

> [!NOTE]
>  Přidání **__declspec(noreturn)** funkci, která se očekává navrácení může vést k nedefinovanému chování.

## <a name="example"></a>Příklad

V následujícím příkladu **else** klauzule neobsahuje příkaz return.  Deklarování `fatal` jako **__declspec(noreturn)** zabrání chybě nebo upozornění.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)