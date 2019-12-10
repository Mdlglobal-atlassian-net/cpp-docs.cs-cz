---
title: marshal_as
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2b2cacb0acf04aa40b3e299bffd7357e04916b16
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988136"
---
# <a name="marshal_as"></a>marshal_as

Tato metoda převádí data mezi nativním a spravovaným prostředím.

## <a name="syntax"></a>Syntaxe

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>Parametry

*vstup*<br/>
pro Hodnota, kterou chcete zařadit do proměnné `To_Type`.

## <a name="return-value"></a>Návratová hodnota

Proměnná typu `To_Type`, která je převedená hodnota `input`.

## <a name="remarks"></a>Poznámky

Tato metoda je zjednodušený způsob, jak převést data mezi nativními a spravovanými typy. Informace o tom, jaké typy dat jsou podporovány, naleznete [v tématu Přehled C++zařazování v ](../dotnet/overview-of-marshaling-in-cpp.md). Některé převody dat vyžadují kontext. Tyto datové typy lze převést pomocí [třídy marshal_context](../dotnet/marshal-context-class.md).

Pokud se pokusíte o zařazení páru datových typů, které nejsou podporovány, `marshal_as` vygeneruje chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Další informace si můžete přečíst v této chybové zprávě. Chyba `C4996` může být vygenerována pro více než jenom nepoužívané funkce. Jedním z příkladů je pokus o zařazení páru datových typů, které nejsou podporovány.

Zařazování knihovny se skládá z několika hlavičkových souborů. Jakýkoli převod vyžaduje pouze jeden soubor, ale pokud potřebujete pro jiné převody, můžete zahrnout další soubory. Chcete-li zjistit, které převody jsou přidruženy k souborům, podívejte se do tabulky v `Marshaling Overview`. Bez ohledu na to, jaký převod chcete udělat, je požadavek na obor názvů vždycky platný.

Vyvolá `System::ArgumentNullException(_EXCEPTION_NULLPTR)`, je-li vstupní parametr null.

## <a name="example"></a>Příklad

Tento příklad zařazování z `const char*` na typ proměnné `System::String`.

```cpp
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

**Hlavičkový soubor:** \<msclr\marshal.h >, \<msclr – \ marshal_windows. h >, \<msclr – \ marshal_cppstd. h > nebo \<msclr – \ marshal_atl. h >

**Obor názvů:** msclr –:: Interop

## <a name="see-also"></a>Viz také:

[Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)
