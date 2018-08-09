---
title: interior_ptr (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a6478e8ee5474687928692763c5231091f7ad1ce
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017016"
---
# <a name="interiorptr-ccli"></a>interior_ptr (C++/CLI)
*Vnitřní ukazatel* deklaruje ukazatel na uvnitř odkazu typu, ale nikoli samotného objektu. Vnitřní ukazatel může odkazovat odkaz na popisovač, typ hodnoty, popisovač zabalený typ, členství spravovaného typu, nebo element spravovaného pole.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 (Neexistují žádné poznámky o této funkci jazyka, které platí pro všechny moduly runtime.)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 (Neexistují žádné poznámky o této funkci jazyka, které se vztahují jenom Windows Runtime.)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/ZW`  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 Následující příklad syntaxe ukazuje vnitřní ukazatel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### <a name="parameters"></a>Parametry  
 *cv_qualifier*  
 **Const** nebo **volatile** kvalifikátory.  
  
 *Typ*  
 Typ *inicializátor*.  
  
 *var*  
 Název **interior_ptr** proměnné.  
  
 *Inicializátor*  
 Člen typu odkazu, element spravovaného pole nebo jakýkoli jiný objekt, který můžete přiřadit na nativní ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Nativní ukazatel není schopen sledovat položku na spravované haldě, který je výsledkem systému uvolňování paměti přesun instancí objektu při změně jeho umístění. Ukazatele na správně odkazování na instanci, modul runtime musí aktualizovat ukazatel na nově umístěné objektu.  
  
 **Interior_ptr** představuje nadmnožinu funkcí nativní ukazatel.  Proto cokoli, co je možné přiřadit na nativní ukazatel lze také přiřadit **interior_ptr**.  Vnitřní ukazatel se nepovoluje provádět stejnou sadu operací, jako nativní ukazatele, včetně porovnání a aritmetiku ukazatele.  
  
 Vnitřní ukazatel lze deklarovat pouze v zásobníku.  Vnitřní ukazatel nelze deklarovat jako člen třídy.  
  
 Protože vnitřních ukazatelů existují pouze v zásobníku, provede převzetí adresy vnitřní ukazatel nespravovaný ukazatel.  
  
 **interior_ptr** má implicitní převod na **bool**, což umožňuje pro jeho použití podmíněné příkazy.  
  
 Informace o tom, jak deklarovat vnitřní ukazatel, který odkazuje na objekt, který nelze přesunout na haldě uvolňování paměti naleznete v tématu [pin_ptr](../windows/pin-ptr-cpp-cli.md).  
  
 **interior_ptr** je v oboru názvů rozhraní příkazového řádku.  Zobrazit [Platform, default a cli obory názvů](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) Další informace.  
  
 Další informace o vnitřních ukazatelů naleznete v tématu  
  
-   [Postupy: Deklarace a použití vnitřních ukazatelů a spravovaných polí (C++/CLI)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [Postupy: Deklarace hodnotových typů s použitím klíčového slova interior_ptr (C++/CLI)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [Postupy: Přetížení funkcí s vnitřními a nativními ukazateli (C++/CLI)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [Postupy: Deklarace vnitřních ukazatelů s použitím klíčového slova const (C++/CLI)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/clr`  
  
### <a name="examples"></a>Příklady  
  
 Následující příklad ukazuje, jak deklarovat a použít vnitřní ukazatel na typ odkazu.  
  
```cpp  
// interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   int data;  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   h_MyClass->data = 1;  
   Console::WriteLine(h_MyClass->data);  
  
   interior_ptr<int> p = &(h_MyClass->data);  
   *p = 2;  
   Console::WriteLine(h_MyClass->data);  
  
   // alternatively  
   interior_ptr<MyClass ^> p2 = &h_MyClass;  
   (*p2)->data = 3;  
   Console::WriteLine((*p2)->data);  
}  
``` 
  
```Output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)