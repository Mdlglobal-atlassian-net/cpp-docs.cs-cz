---
title: __declspec | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __declspec_cpp
dev_langs: C++
helpviewer_keywords: __declspec keyword [C++]
ms.assetid: 832db681-e8e1-41ca-b78c-cd9d265cdb87
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 294f6060ed163906ba4e9eeaca034ab7cbfc1205
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="declspec"></a>__declspec
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Atribut Rozšířené syntaxe pro určení třídy úložiště používá informace `__declspec` – klíčové slovo, které určuje, že instance daného typu je k uložení a atribut třídy úložiště specifické pro společnost Microsoft uvedené níže. Příklady dalších modifikátory třídy úložiště `static` a `extern` klíčová slova. Tato klíčová slova jsou však součástí specifikace ANSI jazyků C a C++ a jako taková nejsou zahrnuta v syntaxi doplňkového atributu. Syntaxe rozšířeného atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyků C a C++.  
  
## <a name="grammar"></a>Gramatika  
 *specifikátor decl*:  
 `__declspec (`  *Rozšířené decl – modifikátor seq*  `)`  
  
 *Rozšířené decl – modifikátor seq*:  
 *Rozšířené modifikátor decl*opt  
  
 *Rozšířené modifikátor decl rozšířené decl – modifikátor seq*  
  
 *Rozšířené modifikátor decl*:  
 `align(` *#* `)`  
  
 `allocate("`*segname*`")`  
  
 `appdomain`  
  
 `code_seg("`*segname*`")`  
  
 `deprecated`  
  
 `dllimport`  
  
 `dllexport`  
  
 `jitintrinsic`  
  
 `naked`  
  
 `noalias`  
  
 `noinline`  
  
 `noreturn`  
  
 `nothrow`  
  
 `novtable`  
  
 `process`  
  
 `property(`{`get=`*get_func_name*&#124;`,put=` *put_func_name*}`)`  
  
 `restrict`  
  
 `safebuffers`  
  
 `selectany`  
  
 `thread`  
  
 `uuid("`*ComObjectGUID*`")`  
  
 Mezera odděluje sekvenci modifikátoru deklarace. Příklady se zobrazí v pozdějších oddílech.  
  
 Tyto atributy třídy úložiště specifické pro společnost Microsoft podporuje rozšířené atribut gramatika: [zarovnat](../cpp/align-cpp.md), [přidělit](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [zastaralé](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [holé](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [proces](../cpp/process.md), [omezit](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), a [vlákno](../cpp/thread.md). Také podporuje tyto atributy objektu COM: [vlastnost](../cpp/property-cpp.md) a [uuid](../cpp/uuid-cpp.md).  
  
 `code_seg`, `dllexport`, `dllimport`, `naked`, `noalias`, `nothrow`, `property`, `restrict`, `selectany`, `thread`, A `uuid` atributy třídy úložiště jsou vlastnosti jenom z deklarace objektu nebo funkce, ke které se použijí. `thread` Atribut má vliv na data a pouze objekty. `naked` Atribut ovlivňuje pouze funkce. `dllimport` a `dllexport` atributy vliv na funkce, data a objekty. `property`, `selectany`, A `uuid` atributy ovlivnit objektů COM.  
  
 `__declspec` Klíčová slova musí být umístěny na začátku prohlášení. Kompilátor ignoruje bez upozornění všechny `__declspec` klíčová slova dává za * nebo & a před identifikátor proměnné v deklaraci.  
  
 A `__declspec` atribut na začátku prohlášení uživatelsky definovaný typ. platí pro proměnnou daného typu. Příklad:  
  
```  
__declspec(dllimport) class X {} varX;  
```  
  
 V takovém případě atribut platí pro `varX`. A `__declspec` atribut dává za `class` nebo `struct` – klíčové slovo platí pro typ definovaný uživatelem. Příklad:  
  
```  
class __declspec(dllimport) X {};  
```  
  
 V takovém případě atribut platí pro `X`.  
  
 Obecných pokynů pro použití `__declspec` atribut pro jednoduché deklarace vypadá takto:  
  
```  
  
decl-specifier-seq  
declarator-list;  
```  
  
 *Decl. specifikátor seq* by měl obsahovat mimo jiné základní typ (například `int`, `float`, `typedef`, nebo název třídy), třídy úložiště (například `static`, `extern`), nebo `__declspec`rozšíření. *Init. deklarátor seznamu* by měl obsahovat mimo jiné ukazatele část deklarace. Příklad:  
  
```  
__declspec(selectany) int * pi1 = 0;   //OK, selectany & int both part of decl-specifier  
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier  
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator  
```  
  
 Následující kód deklaruje místní proměnnou vlákna integer a inicializuje ji hodnotou:  
  
```  
// Example of the __declspec keyword  
__declspec( thread ) int tls_i = 1;  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)