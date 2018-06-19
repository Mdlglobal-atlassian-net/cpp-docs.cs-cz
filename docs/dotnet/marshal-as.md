---
title: marshal_as | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ebca4a94fa48feb4ff5fb897293303a395ac4eb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133776"
---
# <a name="marshalas"></a>marshal_as
Tato metoda převádí data mezi nativní a spravovaná prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `input`  
 Hodnota, kterou chcete zařazování na `To_Type` proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Proměnné typu `To_Type` tedy převedenou hodnotu `input`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je jednodušší způsob, jak převést data mezi nativní a spravovaná typy. Pokud chcete zjistit, jaké typy dat jsou podporované, najdete v části [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md). Některé konverze datových vyžadují kontextu. Tyto datové typy lze převést pomocí [marshal_context – třída](../dotnet/marshal-context-class.md).  
  
 Pokud se pokusíte zařazování pár typy dat, které nejsou podporovány, `marshal_as` vygenerují chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Přečtěte si zprávy zadaný k této chybě Další informace. `C4996` Pro více než jen zastaralé funkce může být generována chyba. Příkladem toho je pokusu o zařazení pár typy dat, které nejsou podporovány.  
  
 Knihovny zařazování se skládá z několika hlavičkových souborů. Jakékoli převody vyžaduje pouze jeden soubor, ale můžete zahrnout další soubory, pokud je potřeba pro jiné převody. Pokud chcete zjistit, které převody jsou přidruženy soubory, které, podívejte se v tabulce v `Marshaling Overview`. Bez ohledu na to co převod chcete udělat, požadavek na obor názvů je vždy v platnost.  
  
## <a name="example"></a>Příklad  
 Tento příklad zařazuje z `const char*` k `System::String` typ proměnné.  
  
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
 [Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_context Class](../dotnet/marshal-context-class.md)