---
title: Upozornění linkerů LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: 9e52dd533d897e729aba5f2b43ea6c019a024d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182978"
---
# <a name="linker-tools-warning-lnk4224"></a>Upozornění linkerů LNK4224

> *možnost* už není podporovaná; přeskočen

## <a name="remarks"></a>Poznámky

Byla zadána neplatná, zastaralá možnost linkeru a ignorována.

Například LINKERŮ LNK4224 může nastat, pokud se v. obj objeví direktiva/Comment. Direktiva/Comment by se přidala prostřednictvím direktivy pragma [Comment (C++C/)](../../preprocessor/comment-c-cpp.md) s použitím nepoužívané možnosti exestr. Pomocí nástroje DUMPBIN [/All](../../build/reference/all.md) můžete zobrazit direktivy linkeru v souboru. obj.

Pokud je to možné, upravte zdroj objektu. obj a odeberte direktivu pragma. Pokud toto upozornění přeskočíte, je možné, že soubor. executable kompilovaný pomocí **/clr: Pure** nebude spuštěn podle očekávání. Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK4224.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```
