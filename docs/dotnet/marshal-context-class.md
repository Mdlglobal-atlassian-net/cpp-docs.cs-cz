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
ms.openlocfilehash: 25fc2be80ba0e5d8c7f76cee1f22eed4d1bb4fc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384865"
---
# <a name="marshalcontext-class"></a>marshal_context – třída

Tato třída převádí data mezi nativními a spravovanými prostředími.

## <a name="syntax"></a>Syntaxe

```cpp
class marshal_context
```

## <a name="remarks"></a>Poznámky

Použití `marshal_context` třídu pro převodů dat, které vyžadují kontextu. Další informace o převody, které vyžadují kontextu a soubor, který zařazování musí být součástí najdete v tématu [přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md). Výsledek zařazování při použití kontextu je platný pouze dokud `marshal_context` objekt zničen. Pro zachování vašich výsledek, je nutné zkopírovat data.

Stejné `marshal_context` lze použít pro množství dat převody. Opětovné použití kontextu tímto způsobem nebude mít vliv na výsledky z předchozího volání zařazování.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis| 
|---------|-----------| 
|[marshal_context::marshal_context](#marshal-context)|Vytvoří `marshal_context` objektu, který chcete použít pro převod dat mezi spravovaným a nativním datové typy.| 
|[marshal_context::~marshal_context](#tilde-marshal-context)|Odstraní `marshal_context` objektu.| 

### <a name="public-methods"></a>Veřejné metody

|Název|Popis| 
|---------|-----------| 
|[marshal_context::marshal_as](#marshal-as)|Provádí zařazování na konkrétní datový objekt k převodu mezi spravovaný a nativní datovým typem.| 


## <a name="requirements"></a>Požadavky

**Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="marshal-context"></a>marshal_context::marshal_context

Vytvoří `marshal_context` objektu, který chcete použít pro převod dat mezi spravovaným a nativním datové typy.

```cpp
marshal_context();
```

### <a name="remarks"></a>Poznámky

Některé převodů dat vyžadují zařazování kontextu. Další informace o tom, které vyžadují překlady kontextu a které zařazování souborů musí zahrnovat ve vaší aplikaci naleznete v tématu [přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).


## <a name="tilde-marshal-context"></a>marshal_context –:: ~ marshal_context –

Odstraní `marshal_context` objektu.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Poznámky

Některé převodů dat vyžadují zařazování kontextu. Zobrazit [přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o překlady, které vyžadují kontextu a které zařazování soubor musí být součástí vaší aplikace.

Odstranění `marshal_context` objekt zruší platnost dat převedených pomocí daného kontextu. Pokud chcete zachovat data po `marshal_context` objekt je zničen, musíte ručně zkopírovat data do proměnné, která se zachová.

## <a name="marshal-as"></a>marshal_context::marshal_as

Provádí zařazování na konkrétní datový objekt k převodu mezi spravovaný a nativní datovým typem.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parametry

*Vstup*<br/>
[in] Hodnota, kterou chcete zařadit na `To_Type` proměnné.

### <a name="return-value"></a>Návratová hodnota

Proměnné typu `To_Type` , která je převedená hodnota `input`.

### <a name="remarks"></a>Poznámky

Tato funkce provede zařazování na konkrétní datový objekt. Tuto funkci použít pouze s převody uvedené v tabulce v [přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md).

Pokud se pokusíte zařazování pár datových typů, které nejsou podporované. zahrnuje `marshal_as` vygeneruje chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Přečtěte si zprávy zadané k této chybě Další informace. `C4996` Chyby mohou být generovány pro více než jen zastaralé funkce. Jsou dvě podmínky, které generují tato chyba pokusu o zařazení pár datových typů, které nejsou podporovány a pokusu o použití `marshal_as` pro převod, který vyžaduje kontext.

Zařazovací knihovna se skládá z několika hlavičkové soubory. Jakýkoli převod vyžaduje pouze jeden soubor, ale pokud je potřeba pro ostatní převody, které můžete zahrnout další soubory. V tabulce v `Marshaling Overview in C++` označuje zařazování soubor, který by měl být zahrnutý pro každý převod.

### <a name="example"></a>Příklad

Tento příklad vytvoří kontext pro zařazování z `System::String` k `const char *` typ proměnné. Převedená data nebudou po řádek, který odstraní kontextu platný.

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