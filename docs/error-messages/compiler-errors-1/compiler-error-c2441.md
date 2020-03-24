---
title: Chyba kompilátoru C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 4e5d5335717ec77c61069ad08e209f9e1851dc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205306"
---
# <a name="compiler-error-c2441"></a>Chyba kompilátoru C2441

> '*Variable*': symbol deklarovaný pomocí __declspec (Process) musí být const v režimu/CLR: Pure.

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Ve výchozím nastavení jsou proměnné na doménu aplikace pod možností **/clr: Pure**. Proměnná označená `__declspec(process)` v **/clr: Pure** je náchylná k chybám, pokud se změnila v jedné doméně aplikace a načte se v jiné.

Proto kompilátor vynutil proměnné procesu je `const` v režimu **/clr: Pure**, aby je bylo možné číst pouze ve všech doménách aplikace.

Další informace naleznete v tématu [Process](../../cpp/process.md) and [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
