---
title: Chyba linkerů LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 096ccb7ff443d24e0d53e73a5950faa1e85aeae6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194561"
---
# <a name="linker-tools-error-lnk2031"></a>Chyba linkerů LNK2031

> Nepovedlo se vygenerovat p/Invoke pro:*function_declaration* *decorated_name*; v metadatech chybí konvence volání.

## <a name="remarks"></a>Poznámky

Při pokusu o import nativní funkce do čistě image mějte na paměti, že konvence implicitního volání se liší mezi nativním a čistým kompilací. Další informace o čistých bitových kopiích naleznete v tématu [čistý aC++ověřitelný kód (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

## <a name="example"></a>Příklad

Tato ukázka kódu vygeneruje komponentu s exportovanou, nativní funkcí, jejíž konvence volání je implicitně [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Příklad

Následující ukázka vytvoří čistě klienta, který využívá nativní funkci. Nicméně konvence volání v rámci **/clr: Pure** je [__clrcall](../../cpp/clrcall.md). Následující ukázka generuje LINKERŮ LNK2031.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít nativní funkci z čistě obrázku. Všimněte si explicitního specifikátoru konvence volání **__cdecl** .

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
