---
title: Dvojitý převod adres (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 47d5bbbecc8e1b9743c543a503df1a0afa0dc0ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="double-thunking-c"></a>Dvojitý převod adres na jinou bitovou šířku (C++)
Dvojitý převod adres odkazuje ke ztrátě výkonu, které se mohou vyskytnout při volání funkce ve spravovaném kontextu volání Visual C++ spravovat funkce a kde provádění programu volá nativní vstupní bod funkce k volání spravované funkce. Toto téma popisuje, kde probíhá dvojitý převod adres a jak se můžete vyhnout ji ke zlepšení výkonu.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, když kompilujete s **/CLR**, definice spravované funkce způsobí, že kompilátor vygeneruje spravovaný vstupní bod a nativní vstupní bod. To umožňuje spravované funkce k volání z nativní a spravovaná volání lokalit. Ale když existuje nativní vstupní bod, může být vstupní bod pro všechna volání funkce. Pokud volání funkce spravované, nativní vstupní bod zavolá spravované vstupní bod. V důsledku toho jsou potřeba k vyvolání funkce dvě volání (proto tedy dvojitý převod adres). Virtuální funkce jsou vždy volány prostřednictvím nativního vstupního bodu.  
  
 Jedním řešením je říct kompilátoru generování nativní vstupní bod pro spravovanou funkci, že funkci bude možné volat jedině z spravovaného kontextu pomocí [__clrcall](../cpp/clrcall.md) konvence volání.  
  
 Podobně pokud chcete exportovat ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) spravovanou funkci, je generován nativní vstupní bod a všechny funkce, která importuje a volání této funkce bude volat prostřednictvím nativního vstupního bodu. Abyste se vyhnuli dvojitý převod adres v této situaci, nepoužívejte sémantiky nativní exportu/importu; jednoduše odkazujte metadata prostřednictvím `#using` (viz [#using – direktiva](../preprocessor/hash-using-directive-cpp.md)).  
  
 Kompilátor byla aktualizována ke snížení nepotřebné dvojitý převod adres. Například všechny funkce spravovaného typu v podpis (včetně návratový typ) budou implicitně označeny jako `__clrcall`. Další informace o dvojité jinou bitovou šířku, najdete v části [ http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, dvojitý převod adres. Při nativní kompilaci (bez **/CLR**), volání virtuální funkce v `main` generuje jednoho volání `T`na kopírování konstruktor a jedno volání destruktoru. Podobné chování se dosáhne, když je virtuální funkce deklarována s **/CLR** a `__clrcall`. Ale když právě kompilujete s **/CLR**, volání funkce generuje volání konstruktor copy, ale další volání konstruktoru kopírování z důvodu převodu nativní spravované.  
  
### <a name="code"></a>Kód  
  
```  
// double_thunking.cpp  
// compile with: /clr  
#include <stdio.h>  
struct T {  
   T() {  
      puts(__FUNCSIG__);  
   }  
  
   T(const T&) {  
      puts(__FUNCSIG__);  
   }  
  
   ~T() {  
      puts(__FUNCSIG__);  
   }  
  
   T& operator=(const T&) {  
      puts(__FUNCSIG__);  
      return *this;  
   }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
  
   printf("calling struct S\n");  
   pS->f(t);  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>Vzorový výstup  
  
```  
__thiscall T::T(void)  
calling struct S  
__thiscall T::T(const struct T &)  
__thiscall T::T(const struct T &)  
__thiscall T::~T(void)  
__thiscall T::~T(void)  
after calling struct S  
__thiscall T::~T(void)  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Předchozí příklad ukazuje existenci dvojitý převod adres. Tento příklad ukazuje její vliv. `for` Smyčky volá funkci virtuální a čas provádění programu sestavy. Nejpomalejší čas je hlášené, když je program kompilovat s **/CLR**. Při kompilování bez vznikly nejrychlejší časy **/CLR** nebo pokud je virtuální funkce deklarována s `__clrcall`.  
  
### <a name="code"></a>Kód  
  
```  
// double_thunking_2.cpp  
// compile with: /clr  
#include <time.h>  
#include <stdio.h>   
  
#pragma unmanaged  
struct T {  
   T() {}  
   T(const T&) {}  
   ~T() {}  
   T& operator=(const T&) { return *this; }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
   clock_t start, finish;  
   double  duration;  
   start = clock();  
  
   for ( int i = 0 ; i < 1000000 ; i++ )  
      pS->f(t);  
  
   finish = clock();  
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);  
   printf( "%2.1f seconds\n", duration );  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>Vzorový výstup  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)