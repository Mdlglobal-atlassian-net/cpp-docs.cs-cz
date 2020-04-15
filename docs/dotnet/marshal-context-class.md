---
title: marshal_context – třída
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 110fe4abf7eb90b05e7feef563efa4882bed0fc6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332016"
---
# <a name="marshal_context-class"></a>marshal_context – třída

Tato třída převádí data mezi nativním a spravovaným prostředím.

## <a name="syntax"></a>Syntaxe

```cpp
class marshal_context
```

## <a name="remarks"></a>Poznámky

Třídu `marshal_context` použijte pro převody dat, které vyžadují kontext. Další informace o tom, které převody vyžadují kontext a který zařazovací soubor musí být zahrnut, naleznete [v tématu Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md). Výsledek zařazování při použití kontextu je `marshal_context` platný pouze do zničení objektu. Chcete-li zachovat výsledek, je nutné zkopírovat data.

Totéž `marshal_context` lze použít pro mnoho převodů dat. Opětovné použití kontextu tímto způsobem nebude mít vliv na výsledky z předchozích volání zařazování.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejní konstruktéři

|Name (Název)|Popis|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Vytvoří objekt, `marshal_context` který se použije pro převod dat mezi spravovanými a nativními datovými typy.|
|[marshal_context::~marshal_context](#tilde-marshal-context)|Zničí `marshal_context` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Provádí zařazování na konkrétní datový objekt převést mezi spravované a nativní datový typ.|

## <a name="requirements"></a>Požadavky

**Soubor záhlaví:** \<msclr\marshal.h \<>, msclr\marshal_windows.h>, \<msclr\marshal_cppstd.h> nebo \<msclr\marshal_atl.h>

**Obor názvů:** msclr::interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context::marshal_context

Vytvoří objekt, `marshal_context` který se použije pro převod dat mezi spravovanými a nativními datovými typy.

```cpp
marshal_context();
```

### <a name="remarks"></a>Poznámky

Některé převody dat vyžadují kontext marshal. Další informace o tom, které překlady vyžadují kontext a který zařazovací soubor je třeba zahrnout do aplikace, naleznete v [tématu Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Příklad

Viz příklad pro [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context::~marshal_context

Zničí `marshal_context` objekt.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Poznámky

Některé převody dat vyžadují kontext marshal. Další informace o tom, které překlady vyžadují kontext a který zařazovací soubor musí být zahrnut do aplikace, naleznete [v tématu Přehled zařazování v jazyce C++.](../dotnet/overview-of-marshaling-in-cpp.md)

Odstraněníobjektu `marshal_context` zruší platnost dat převedených tímto kontextem. Pokud chcete zachovat data po `marshal_context` zničení objektu, je nutné ručně zkopírovat data do proměnné, která bude přetrvávat.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context::marshal_as

Provádí zařazování na konkrétní datový objekt převést mezi spravované a nativní datový typ.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parametry

*Vstupní*<br/>
[v] Hodnota, kterou chcete zařadit do `To_Type` proměnné.

### <a name="return-value"></a>Návratová hodnota

Proměnná typu, `To_Type` která je převedenou `input`hodnotou .

### <a name="remarks"></a>Poznámky

Tato funkce provádí zařazování na konkrétní datový objekt. Tuto funkci používejte pouze s převody označenými v tabulce v [přehledu zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md).

Pokud se pokusíte zařadit dvojici datových `marshal_as` typů, které nejsou podporovány, vygeneruje chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Další informace naleznete ve zprávě dodané s touto chybou. Chyba `C4996` může být generována pro více než jen zastaralé funkce. Dvě podmínky, které generují tuto chybu se snaží zařadit dvojici datových typů, které nejsou podporovány a pokusu o použití `marshal_as` pro převod, který vyžaduje kontext.

Zařazovací knihovna se skládá z několika souborů hlaviček. Jakýkoli převod vyžaduje pouze jeden soubor, ale v případě potřeby můžete zahrnout další soubory pro jiné převody. Tabulka v `Marshaling Overview in C++` označuje, který zařazovací soubor by měl být zahrnut pro každý převod.

### <a name="example"></a>Příklad

Tento příklad vytvoří kontext pro `System::String` zařazování z `const char *` typu proměnné. Převedená data nebudou platná po řádku, který odstraní kontext.

```cpp
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```
