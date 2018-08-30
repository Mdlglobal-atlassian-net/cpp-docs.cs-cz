---
title: Převáděcího Double (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 3e37b3b7fc477de0bdbeb00a15ebd86e6c44d25c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216634"
---
# <a name="double-thunking-c"></a>Dvojitý převod adres na jinou bitovou šířku (C++)
Dvojitému odkazuje na dojít ke ztrátě výkonu, které se mohou vyskytnout při volání funkce v kontextu spravovaných volání Visual C++, spravovat funkce a kde provádění programu volání funkce nativní vstupní bod pro volání spravované funkce. Toto téma popisuje, kde dochází k dvojitému a jak se můžete vyhnout je k vylepšení výkonu.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení při kompilaci s **/CLR**, definici spravované funkce způsobí, že kompilátor generovat spravovaný vstupní bod a nativní vstupní bod. To umožňuje spravované funkce lze volat z lokalit nativního a spravovaného volání. Ale pokud mezi doménami existuje nativní vstupní bod, může být vstupní bod pro všechna volání funkce. Pokud je volání funkce spravované, nativní vstupní bod zavolá spravovaný vstupní bod. V důsledku toho jsou dvě volání požadovaných pro vyvolání funkce (proto tedy dvojitý převod adres). Virtuální funkce jsou vždy volá prostřednictvím nativní vstupní bod.  
  
 Jedním řešením je předat kompilátoru generování nativní vstupní bod pro spravované funkce, funkce zavolá jenom ze spravovaných kontextu pomocí [__clrcall](../cpp/clrcall.md) konvence volání.  
  
 Podobně pokud exportujete ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) spravované funkce se generuje nativní vstupní bod a všechny funkce, které importuje a volání této funkce bude volat přes nativní vstupní bod. Chcete-li zabránit dvojitému v této situaci, nepoužívejte sémantiky exportu/importu nativní; na ně jednoduše odkázat metadat prostřednictvím `#using` (viz [# direktiva using](../preprocessor/hash-using-directive-cpp.md)).  
  
 Aktualizovali jsme kompilátor snížit nepotřebné dvojitému. Například všechny funkce se spravovaným typem v podpisu (včetně návratový typ) bude implicitně označeny jako `__clrcall`. Další informace o double jinou bitovou šířku, naleznete v tématu [ https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje dvojitému. Při nativní kompilaci (bez **/CLR**), volání virtuální funkce v `main` vygeneruje volání `T`pro kopírování, konstruktor a destruktor volání. Podobného chování se dosáhne, když je virtuální funkce deklarována s **/CLR** a `__clrcall`. Ale při kompilaci pouze s **/CLR**, volání funkce vygeneruje volání kopie konstruktoru, ale existuje další volání konstruktoru kopie z důvodu převodní rutina nativní spravované.  
  
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
 Předchozí příklad ukazuje existenci dvojitému. Tento příklad ukazuje jeho vliv. `for` Smyčky volání virtuální funkce a doba provádění sestavy programu. Nejpomalejší dobu je hlášené, když je program zkompilován s **/CLR**. Nejrychlejší doby jsou hlášeny při kompilaci bez **/CLR** nebo pokud virtuální funkce je deklarována s `__clrcall`.  
  
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