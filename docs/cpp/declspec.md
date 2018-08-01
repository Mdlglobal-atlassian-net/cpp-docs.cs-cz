---
title: __declspec | Dokumentace Microsoftu
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
ms.openlocfilehash: 4358712e5573095229a48a6d08b78706c608874d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403645"
---
# <a name="declspec"></a>__declspec

**Specifické pro Microsoft**

Syntaxe rozšířeného atributu pro určení informací o třídě úložiště používá **__declspec** – klíčové slovo, které určuje, že instance daného typu uloží v rámci níže uvedeného atributu třídy úložiště specifické pro společnost Microsoft. Příklady dalších modifikátorů na úložiště **statické** a **extern** klíčová slova. Tato klíčová slova jsou však součástí specifikace ANSI jazyků C a C++ a jako taková nejsou zahrnuta v syntaxi doplňkového atributu. Syntaxe rozšířeného atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyků C a C++.

## <a name="grammar"></a>Gramatika

*decl-specifier*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*Extended-decl-modifier-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl modifikátor*<sub>optimalizované</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl modifikátor* *extended-decl-modifier-seq*

*Extended-decl modifikátor*:  
&nbsp;&nbsp;&nbsp;&nbsp;**zarovnání (** *#* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**přidělit ("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**domény aplikace**  
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**zastaralé**  
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**  
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**  
&nbsp;&nbsp;&nbsp;&nbsp;**naked**  
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**  
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**  
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**  
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**  
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**  
&nbsp;&nbsp;&nbsp;&nbsp;**Proces**  
&nbsp;&nbsp;&nbsp;&nbsp;**vlastnosti (** { **získat =**_get_func_name_ &#124; **, vložení =**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**omezení**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**vlákno**  
&nbsp;&nbsp;&nbsp;&nbsp;**UUID ("** *ComObjectGUID* **")**  

Mezera odděluje sekvenci modifikátoru deklarace. Příklady se zobrazí v pozdějších oddílech.

Rozšířený atribut gramatiky podporuje tyto atributy třídy úložiště specifické pro společnost Microsoft: [zarovnat](../cpp/align-cpp.md), [přidělit](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [zastaralé](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [procesu](../cpp/process.md), [omezit](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [chyby zabezpečení spectre](../cpp/spectre.md), a [vlákno](../cpp/thread.md). Také podporuje tyto atributy objektu COM: [vlastnost](../cpp/property-cpp.md) a [uuid](../cpp/uuid-cpp.md).

**Code_seg**, **dllexport**, **dllimport**, **naked**, **noalias**, **nothrow** , **vlastnost**, **omezit**, **selectany**, **vlákno**, a **uuid**atributy třídy úložiště jsou vlastnosti pouze prohlášení objektu nebo funkce, do které se použijí. **Vlákno** atribut má vliv na data a pouze objekty. **Naked** a **chyby zabezpečení spectre** atributy ovlivňují pouze funkce. **Dllimport** a **dllexport** ovlivňují atributy funkce, data a objekty. **Vlastnost**, **selectany**, a **uuid** objekty COM ovlivňují atributy.

**__Declspec** klíčová slova, umístit na začátek jednoduchého prohlášení. Kompilátor ignoruje bez varování všechna **__declspec** klíčová slova umístí po * nebo & a před identifikátorem proměnné v deklaraci.

A **__declspec** atribut na začátku deklarace uživatelského typu platí pro proměnnou daného typu. Příklad:

```cpp
__declspec(dllimport) class X {} varX;
```

V tomto případě platí atribut pro `varX`. A **__declspec** atribut umístěný za **třídy** nebo **struktura** – klíčové slovo platí pro typ definovaný uživatelem. Příklad:

```cpp
class __declspec(dllimport) X {};
```

V tomto případě platí atribut pro `X`.

Obecný návod pro použití **__declspec** atribut pro jednoduché deklarace je následující:

*decl-specifier-seq* *init-declarator-list*;

*Decl-specifier-seq* by měl obsahovat mimo jiné i základní typ (například **int**, **float**, **typedef**, nebo název třídy), Třída úložiště (třeba **statické**, **extern**), nebo **__declspec** rozšíření. *Init-declarator-list* by měl obsahovat mimo jiné část deklarace s ukazatelem. Příklad:

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:
 [Klíčová slova](../cpp/keywords-cpp.md)  
 [Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)  