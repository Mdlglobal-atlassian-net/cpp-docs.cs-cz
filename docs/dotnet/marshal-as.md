---
title: marshal_as
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: a30f86a41917419474f93a915b92d125112ec7ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492189"
---
# <a name="marshalas"></a>marshal_as

Tato metoda převádí data mezi nativními a spravovanými prostředími.

## <a name="syntax"></a>Syntaxe

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Parametry

*Vstup*<br/>
[in] Hodnota, kterou chcete zařadit na `To_Type` proměnné.

## <a name="return-value"></a>Návratová hodnota

Proměnné typu `To_Type` , který je převedená hodnota `input`.

## <a name="remarks"></a>Poznámky

Tato metoda je jednodušší způsob, jak převést dat mezi nativními a spravovanými typy. Pokud chcete zjistit, jaké typy dat jsou podporovány, naleznete v tématu [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md). Některé převodů dat vyžadují kontextu. Tyto typy dat můžete převádět pomocí [marshal_context Class](../dotnet/marshal-context-class.md).

Pokud se pokusíte zařazování pár datových typů, které nejsou podporované. zahrnuje `marshal_as` vygeneruje chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Přečtěte si zprávy zadané k této chybě Další informace. `C4996` Chyby mohou být generovány pro více než jen zastaralé funkce. Jedním z příkladů je pokusu o zařazení pár datových typů, které nejsou podporovány.

Zařazovací knihovna se skládá z několika hlavičkové soubory. Jakýkoli převod vyžaduje pouze jeden soubor, ale pokud je potřeba pro ostatní převody, které můžete zahrnout další soubory. Pokud chcete zjistit, které převody jsou přidruženy soubory, které, podívejte se v tabulce v `Marshaling Overview`. Bez ohledu na to co převodu chcete udělat, požadavek na obor názvů je vždy v platnosti.

## <a name="example"></a>Příklad

V tomto příkladu zařazuje z `const char*` k `System::String` typ proměnné.

```
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>Požadavky

**Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Viz také

[Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)