---
title: __declspec | Microsoft Docs
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c610da3545e7269c307542930140616dc6af9dce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418286"
---
# <a name="declspec"></a>__declspec

**Konkrétní Microsoft**

Atribut Rozšířené syntaxe pro určení třídy úložiště používá informace **__declspec** – klíčové slovo, které určuje, že instance daného typu je k uložení a atribut třídy úložiště specifické pro společnost Microsoft uvedené níže. Příklady dalších modifikátory třídy úložiště **statické** a **extern** klíčová slova. Tato klíčová slova jsou však součástí specifikace ANSI jazyků C a C++ a jako taková nejsou zahrnuta v syntaxi doplňkového atributu. Syntaxe rozšířeného atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyků C a C++.

## <a name="grammar"></a>Gramatika

*specifikátor decl*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*Rozšířené decl – modifikátor seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Rozšířené modifikátor decl*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*Rozšířené modifikátor decl* *rozšířené decl – modifikátor seq*

*Rozšířené modifikátor decl*:  
&nbsp;&nbsp;&nbsp;&nbsp;**Zarovnat (** *#* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**přidělit ("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**domény aplikace**  
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**Zastaralé**  
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**  
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**  
&nbsp;&nbsp;&nbsp;&nbsp;**holé**  
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**  
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**  
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**  
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**  
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**  
&nbsp;&nbsp;&nbsp;&nbsp;**Proces**  
&nbsp;&nbsp;&nbsp;&nbsp;**vlastnost (** { **získat =**_get_func_name_ &#124; **, put =**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**Omezení**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**Přístup z více vláken**  
&nbsp;&nbsp;&nbsp;&nbsp;**UUID ("** *ComObjectGUID* **")**  

Mezera odděluje sekvenci modifikátoru deklarace. Příklady se zobrazí v pozdějších oddílech.

Tyto atributy třídy úložiště specifické pro společnost Microsoft podporuje rozšířené atribut gramatika: [zarovnat](../cpp/align-cpp.md), [přidělit](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [zastaralé](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [holé](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [proces](../cpp/process.md), [omezit](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [spektrum](../cpp/spectre.md), a [vlákno](../cpp/thread.md). Také podporuje tyto atributy objektu COM: [vlastnost](../cpp/property-cpp.md) a [uuid](../cpp/uuid-cpp.md).

**Code_seg**, **dllexport**, **dllimport**, **holé**, **noalias**, **nothrow** , **vlastnost**, **omezit**, **selectany**, **vlákno**, a **uuid**atributy třídy úložiště jsou pouze vlastnosti deklarace objektu nebo funkce, ke které se použijí. **Vlákno** atribut má vliv na data a pouze objekty. **Holé** a **spektrum** atributy ovlivnit pouze funkce. **Dllimport** a **dllexport** atributy vliv na funkce, data a objekty. **Vlastnost**, **selectany**, a **uuid** atributy ovlivnit objektů COM.

**__Declspec** klíčová slova musí být umístěny na začátku prohlášení. Kompilátor ignoruje bez upozornění všechny **__declspec** klíčová slova dává za * nebo & a před identifikátor proměnné v deklaraci.

A **__declspec** atribut na začátku prohlášení uživatelsky definovaný typ. platí pro proměnnou daného typu. Příklad:

```cpp
__declspec(dllimport) class X {} varX;
```

V takovém případě atribut platí pro `varX`. A **__declspec** atribut dává za **– třída** nebo **struktura** – klíčové slovo platí pro typ definovaný uživatelem. Příklad:

```cpp
class __declspec(dllimport) X {};
```

V takovém případě atribut platí pro `X`.

Obecných pokynů pro použití **__declspec** atribut pro jednoduché deklarace vypadá takto:

*decl. specifikátor seq* *init. deklarátor seznamu*;

*Decl. specifikátor seq* by měl obsahovat mimo jiné základní typ (například **int**, **float**, **typedef**, nebo název třídy), třídy úložiště (například **statické**, **extern**), nebo **__declspec** rozšíření. *Init. deklarátor seznamu* by měl obsahovat mimo jiné ukazatele část deklarace. Příklad:

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

Následující kód deklaruje místní proměnnou vlákna integer a inicializuje ji hodnotou:

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)  
[Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)  
