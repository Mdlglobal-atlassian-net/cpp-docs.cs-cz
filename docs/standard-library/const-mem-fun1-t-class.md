---
title: "const_mem_fun1_t – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::const_mem_fun1_t
dev_langs: C++
helpviewer_keywords: const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 788f49d3aa4cefd46e5ea97517a02a35a9747403
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t – třída
Třídu adaptér, který umožňuje **const** – členská funkce, které přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>  
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```  
  
#### <a name="parameters"></a>Parametry  
 `_Pm`  
 Ukazatel na funkci člena třídy **typ** má být převeden na objekt funkce.  
  
 `_Pleft`  
 **Const** objektu, který `_Pm` – členská funkce je volána v.  
  
 `right`  
 Argument, který se na `_Pm`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Přizpůsobitelné binární funkce.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy ukládá kopie `_Pm`, která musí být ukazatel na funkci člena třídy **typu**, v objektu privátního člena. Definuje jeho – členská funkce `operator()` jako vrácení ( **_Pleft** -> \* *Pm) (***vpravo**) **const**.  
  
## <a name="example"></a>Příklad  
 Konstruktoru `const_mem_fun1_t` se obvykle nepoužívá přímo; pomocné funkce `mem_fun` slouží k přizpůsobení členské funkce. V tématu [mem_fun –](../standard-library/functional-functions.md#mem_fun) příklad použití členské funkce adaptéry.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



