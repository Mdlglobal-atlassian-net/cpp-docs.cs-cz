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
ms.openlocfilehash: 7fb22754248e66d7a20292af41a8e1b8ba050451
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080036"
---
# <a name="marshal_context-class"></a>marshal_context – třída

Tato třída převádí data mezi nativním a spravovaným prostředím.

## <a name="syntax"></a>Syntaxe

```cpp
class marshal_context
```

## <a name="remarks"></a>Poznámky

Použijte třídu `marshal_context` pro převody dat, které vyžadují kontext. Další informace o tom, které převody vyžadují kontext a který soubor zařazování musí být zahrnut, najdete [v tématu Přehled zařazování v C++ ](../dotnet/overview-of-marshaling-in-cpp.md). Výsledek zařazování při použití kontextu je platný pouze v případě, že je objekt `marshal_context` zničen. Chcete-li zachovat výsledek, je nutné zkopírovat data.

Stejný `marshal_context` lze použít pro velký počet převodů dat. Použití kontextu tímto způsobem nebude mít vliv na výsledky z předchozích zařazování volání.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Vytvoří objekt `marshal_context`, který se má použít pro převod dat mezi spravovanými a nativními datovými typy.|
|[marshal_context::~marshal_context](#tilde-marshal-context)|Odstraní objekt `marshal_context`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Provede zařazování na konkrétní datový objekt pro převod mezi spravovaným a nativním datovým typem.|

## <a name="requirements"></a>Požadavky

**Hlavičkový soubor:** \<msclr\marshal.h >, \<msclr – \ marshal_windows. h >, \<msclr – \ marshal_cppstd. h > nebo \<msclr – \ marshal_atl. h >

**Obor názvů:** msclr –:: Interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context:: marshal_context

Vytvoří objekt `marshal_context`, který se má použít pro převod dat mezi spravovanými a nativními datovými typy.

```cpp
marshal_context();
```

### <a name="remarks"></a>Poznámky

Některé převody dat vyžadují zařazovací kontext. Další informace o tom, které překlady vyžadují kontext a který soubor zařazování musíte zahrnout do vaší aplikace, najdete v tématu [Přehled zařazování v C++ ](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Příklad

Podívejte se na příklad [marshal_context:: marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context:: ~ marshal_context

Odstraní objekt `marshal_context`.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Poznámky

Některé převody dat vyžadují zařazovací kontext. Další informace o tom, které překlady vyžadují kontext a který musí být zahrnut do vaší aplikace, najdete v tématu [Přehled zařazování C++ ](../dotnet/overview-of-marshaling-in-cpp.md) .

Odstraněním objektu `marshal_context` dojde k neplatnosti dat převedených kontextem. Chcete-li zachovat data po zničení objektu `marshal_context`, je nutné ručně zkopírovat data do proměnné, která bude zachována.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context:: marshal_as

Provede zařazování na konkrétní datový objekt pro převod mezi spravovaným a nativním datovým typem.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parametry

*vstup*<br/>
pro Hodnota, kterou chcete zařadit do proměnné `To_Type`.

### <a name="return-value"></a>Návratová hodnota

Proměnná typu `To_Type`, která je převedená hodnota `input`.

### <a name="remarks"></a>Poznámky

Tato funkce provádí zařazování na konkrétním datovém objektu. Tuto funkci použijte pouze s převody uvedenými v tabulce v článku [Přehled zařazování v C++ ](../dotnet/overview-of-marshaling-in-cpp.md).

Pokud se pokusíte o zařazení páru datových typů, které nejsou podporovány, `marshal_as` vygeneruje chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Další informace si můžete přečíst v této chybové zprávě. Chyba `C4996` může být vygenerována pro více než jenom nepoužívané funkce. Dvě podmínky, které generují tuto chybu, se pokoušejí zařadit dvojici datových typů, které nejsou podporované a snaží se použít `marshal_as` pro převod, který vyžaduje kontext.

Zařazování knihovny se skládá z několika hlavičkových souborů. Jakýkoli převod vyžaduje pouze jeden soubor, ale pokud potřebujete pro jiné převody, můžete zahrnout další soubory. Tabulka v `Marshaling Overview in C++` určuje, který soubor k zařazování by měl být zahrnut pro každý převod.

### <a name="example"></a>Příklad

Tento příklad vytvoří kontext pro zařazování z `System::String` do typu proměnné `const char *`. Převedená data budou platná za řádkem, který odstraní kontext.

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