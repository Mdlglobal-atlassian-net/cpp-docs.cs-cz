---
title: interior_ptr (C + +/ CLI) | Microsoft Docs
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
ms.openlocfilehash: a83182151ccb85b920a37713b70df53b383b8919
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879104"
---
# <a name="interiorptr-ccli"></a>interior_ptr (C++/CLI)
*Vnitřní ukazatel* deklaruje ukazatel na uvnitř odkazového typu, ale ne samotný objekt. Vnitřní ukazatel můžete bodu odkaz popisovač, typ hodnoty, zabalený typ popisovače, členem spravovaný typ, nebo element spravované pole.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 (Používají se žádné poznámky pro tuto funkci jazyka, které platí pro všechny moduly runtime.)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 (Existují žádné poznámky pro tuto funkci jazyka, která se týkají jenom prostředí Windows Runtime).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 Následující příklad syntaxe ukazuje vnitřní ukazatel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### <a name="parameters"></a>Parametry  
 *cv_qualifier*  
 **Const** nebo `volatile` kvalifikátory.  
  
 *Typ*  
 Typ *inicializátoru*.  
  
 *var*  
 Název `interior_ptr` proměnné.  
  
 *Inicializátor*  
 Člen odkaz, element spravovaného pole nebo jakýkoliv jiný objekt, který lze přiřadit nativní ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Nativní ukazatel není schopný sledovat položku jako změny jeho umístění na spravovaná halda, který je výsledkem bude systém uvolňování přesunutí instance objektu. Aby ukazatel správně odkazovat na instanci je potřeba aktualizovat ukazatele na objekt nově umístěného modulu runtime.  
  
 `interior_ptr` Představuje nadmnožinou funkce nativní ukazatel.  Proto všechny položky, které lze přiřadit k nativní ukazatel lze také přiřadit `interior_ptr`.  Vnitřní ukazatel oprávněn provádět stejnou sadu operací, jako nativními ukazateli, včetně porovnání a aritmetika ukazatele.  
  
 Vnitřní ukazatel lze deklarovat pouze v zásobníku.  Vnitřní ukazatel nelze deklarovat jako člena třídy.  
  
 Vzhledem k tomu, že vnitřních ukazatelů existují pouze v zásobníku, s ohledem na adresu vnitřního ukazatele poskytuje nespravovaný ukazatel.  
  
 `interior_ptr` má implicitní převod na `bool`, což umožňuje pro jeho použití v podmíněné příkazy.  
  
 Informace o tom, jak deklarace vnitřních ukazatelů, která odkazuje na objekt, který nelze přesunout na haldě uvolňování paměti najdete v tématu [pin_ptr](../windows/pin-ptr-cpp-cli.md).  
  
 `interior_ptr` je v oboru názvů rozhraní příkazového řádku.  V tématu [Platform, default a rozhraní příkazového řádku obory názvů](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) Další informace.  
  
 Další informace o vnitřních ukazatelů najdete v tématu  
  
-   [Postupy: Deklarace a použití vnitřních ukazatelů a spravovaných polí (C++/CLI)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [Postupy: Deklarace hodnotových typů s použitím klíčového slova interior_ptr (C++/CLI)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [Postupy: Přetížení funkcí s vnitřními a nativními ukazateli (C++/CLI)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [Postupy: Deklarace vnitřních ukazatelů s použitím klíčového slova const (C++/CLI)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad ukazuje, jak deklarování a použití vnitřních ukazatelů do odkazového typu.  
  
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
  
 **Output**  
  
```Output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)