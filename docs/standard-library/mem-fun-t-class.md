---
title: "mem_fun_t – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::mem_fun_t
dev_langs: C++
helpviewer_keywords: mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b296e63f3392c6ba9a38116a096d8fd9526103e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="memfunt-class"></a>mem_fun_t – třída
Třídu adaptér, který umožňuje **non_const** – členská funkce, které nepřijímá žádné argumenty, která se má volat jako objekt funkce unární při inicializaci s argumentem ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;

 };
```  
  
#### <a name="parameters"></a>Parametry  
 `_Pm`  
 Ukazatel na funkci člena třídy **typ** má být převeden na objekt funkce.  
  
 `_Pleft`  
 Objekt, `_Pm` – členská funkce je volána v.  
  
## <a name="return-value"></a>Návratová hodnota  
 Přizpůsobitelné unární funkce.  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy ukládá kopie `_Pm`, která musí být ukazatel na funkci člena třídy **typu**, v objektu privátního člena. Definuje jeho – členská funkce `operator()` jako vrácení ( `_Pleft` ->*  `_Pm`) ().  
  
## <a name="example"></a>Příklad  
 Konstruktoru `mem_fun_t` se obvykle nepoužívá přímo; pomocné funkce `mem_fun` slouží k přizpůsobení členské funkce. V tématu [mem_fun –](../standard-library/functional-functions.md#mem_fun) příklad použití členské funkce adaptéry.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<funkční >](../standard-library/functional.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)


