---
title: Závažná chyba nástroje NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367236"
---
# <a name="nmake-fatal-error-u1070"></a>Závažná chyba nástroje NMAKE U1070

zacyklení v definici makra "makro"

Definice makra dané obsažené makra, jejichž definice obsahovala danou – makro. Definice maker cyklické jsou neplatné.

## <a name="example"></a>Příklad

Následující definice – makro

```
ONE=$(TWO)
TWO=$(ONE)
```

způsobit následující chybu:

```
cycle in macro definition 'TWO'
```