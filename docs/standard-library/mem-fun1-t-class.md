---
title: "mem_fun1_t – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6c14f7076c733e00c00d271a329e7e4c7c14efb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="memfun1t-class"></a>mem_fun1_t – třída
Třídu adaptér, který umožňuje **non_const** – členská funkce, které přijímá jeden argument, která se má volat jako objekt binární funkce při inicializaci s argumentem ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

 };
```  
  
#### <a name="parameters"></a>Parametry  
 `_Pm`  
 Ukazatel na funkci člena třídy **typ** má být převeden na objekt funkce.  
  
 `_Pleft`  
 Objekt, `_Pm` – členská funkce je volána v.  
  
 `right`  
 Argument, který se na `_Pm`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Přizpůsobitelné binární funkce.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy ukládá kopie `_Pm`, která musí být ukazatel na funkci člena třídy **typu**, v objektu privátního člena. Definuje jeho – členská funkce `operator()` jako vrácení ( **_Pleft** -> \* `_Pm`) ( **správné**).  
  
## <a name="example"></a>Příklad  
  Konstruktoru `mem_fun1_t` se obvykle nepoužívá přímo; pomocné funkce `mem_fun` slouží k přizpůsobení členské funkce. V tématu [mem_fun –](../standard-library/functional-functions.md#mem_fun) příklad použití členské funkce adaptéry.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



