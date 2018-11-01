---
title: auto_handle::operator bool
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_handle.operator bool
- msclr.auto_handle.operator bool
- operator bool
- msclr::auto_handle::operator bool
- auto_handle::operator bool
helpviewer_keywords:
- auto_handle::operator bool
ms.assetid: 2e535e99-cf87-4008-b588-02c587d77453
ms.openlocfilehash: 95a4b324194b2e1adf8cc9596f8e2440379e5a47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565942"
---
# <a name="autohandleoperator-bool"></a>auto_handle::operator bool

Operátor pro používání `auto_handle` v podmíněných výrazech.

## <a name="syntax"></a>Syntaxe

```
operator bool();
```

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zabalená objektu je platná. **false** jinak.

## <a name="remarks"></a>Poznámky

Tento operátor převede ve skutečnosti na `_detail_class::_safe_bool` což je bezpečnější než **bool** vzhledem k tomu, že jej nelze převést na celočíselný typ.

## <a name="example"></a>Příklad

```
// msl_auto_handle_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "hi";
   if ( s1 ) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\auto_handle.h >

**Namespace** msclr –

## <a name="see-also"></a>Viz také

[auto_handle – členy](../dotnet/auto-handle-members.md)<br/>
[auto_handle::operator!](../dotnet/auto-handle-operator-logical-not.md)