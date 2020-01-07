---
title: Chyba kompilátoru C2099
ms.date: 11/04/2016
f1_keywords:
- C2099
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
ms.openlocfilehash: e9fb7739111d13a585579455ed97cecaca3266e4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301935"
---
# <a name="compiler-error-c2099"></a>Chyba kompilátoru C2099

inicializátor není konstanta.

Tato chyba je vydána pouze kompilátorem jazyka C a probíhá pouze pro proměnné, které nejsou automatické.  Kompilátor inicializuje na začátku programu jiné proměnné než automatické a hodnoty, které jsou inicializovány, musí být konstantní.

## <a name="example"></a>Příklad

Následující ukázka generuje C2099.

```c
// C2099.c
int j;
int *p;
j = *p;   // C2099 *p is not a constant
```

## <a name="example"></a>Příklad

C2099 může také nastat, protože kompilátor nemůže provádět konstantní skládání výrazu v rámci **/FP: Strict** , protože nastavení prostředí přesnosti s plovoucí desetinnou čárkou (viz [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md) pro další informace) se může lišit od kompilace po dobu běhu.

V případě neúspěchu konstantního skládání vyvolá kompilátor dynamickou inicializaci, která není v jazyce C povolena.

Chcete-li tuto chybu vyřešit, zkompilujte modul jako soubor. cpp nebo Zjednodušte výraz.

Další informace najdete v tématu [/FP (určení chování s plovoucí](../../build/reference/fp-specify-floating-point-behavior.md)desetinnou čárkou).

Následující ukázka generuje C2099.

```c
// C2099_2.c
// compile with: /fp:strict /c
float X = 2.0 - 1.0;   // C2099
float X2 = 1.0;   // OK
```
