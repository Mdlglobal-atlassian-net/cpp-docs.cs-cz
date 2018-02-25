---
title: "&lt;výjimka&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 24f4fc5d30a95d55b5a4241d9c70eca31255fc18
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltexceptiongt-typedefs"></a>&lt;výjimka&gt; – definice TypeDef
||||  
|-|-|-|  
|[exception_ptr](#exception_ptr)|[terminate_handler](#terminate_handler)|[unexpected_handler](#unexpected_handler)|  
  
##  <a name="exception_ptr"></a>  exception_ptr  
 Typ, který popisuje ukazatele na výjimku.  
  
```cpp  
typedef unspecified exception_ptr;
```  
  
### <a name="remarks"></a>Poznámky  
 Neurčené interní třída, která se používá k implementaci `exception_ptr` typu.  
  
 Použijte `exception_ptr` objekt, který má odkazovat na aktuální výjimky nebo instanci výjimka zadaného uživatelem. V implementaci společnosti Microsoft, je reprezentována výjimku [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) struktury. Každý `exception_ptr` objekt zahrnuje pole odkazu výjimka, která odkazuje na kopii `EXCEPTION_RECORD` struktura, která představuje výjimku.  
  
 Když je deklarovat `exception_ptr` proměnné, proměnné není přidružen k žádné výjimky. Tedy referenční pole výjimky je NULL. Takové `exception_ptr` objektu se říká *null exception_ptr*.  
  
 Použití `current_exception` nebo `make_exception_ptr` funkce přiřadit výjimku `exception_ptr` objektu. Přiřadíte-li výjimku `exception_ptr` proměnné, pole výjimka odkazu proměnnou odkazuje na kopii této výjimky. Pokud není k dispozici dostatek paměti pro kopírování výjimku, pole výjimka odkazu odkazuje na kopii [std::bad_alloc](../standard-library/bad-alloc-class.md) výjimka. Pokud `current_exception` nebo `make_exception_ptr` funkce nelze zkopírovat výjimku z jiného důvodu, volání funkce **ukončit** funkce CRT ukončíte aktuálním procesu.  
  
 Bez ohledu na jeho název `exception_ptr` objektu není sám sebe. je zde ukazatel. Ho neřídí sémantika ukazatele a nelze jej použít s přístup ke členu ukazatele ( `->`) nebo operátory indirection (*). `exception_ptr` Objekt nemá žádné členy veřejná data nebo členské funkce.  
  
 **Porovnání:**  
  
 Můžete rovno ( `==`) a není rovno ( `!=`) operátory k porovnání dvou `exception_ptr` objekty. Operátory porovnání není binární hodnotu (bitový) `EXCEPTION_RECORD` struktury, které představují výjimky. Místo toho operátory porovnání adresy v poli výjimka odkazu `exception_ptr` objekty. V důsledku toho s hodnotou null `exception_ptr` a porovnání jako rovnocenné hodnotu NULL.  
  
##  <a name="terminate_handler"></a>  terminate_handler  
 Popisuje typ ukazatel na funkci, která je vhodná pro použití jako `terminate_handler`.  
  
```
typedef void (*terminate_handler)();
```  
  
### <a name="remarks"></a>Poznámky  
 Typ, který popisuje ukazatele na funkci vhodný pro použití jako obslužná rutina ukončení.  
  
### <a name="example"></a>Příklad  
  V tématu [set_terminate –](../standard-library/exception-functions.md#set_terminate) příklad použití `terminate_handler`.  
  
##  <a name="unexpected_handler"></a>  unexpected_handler  
 Popisuje typ ukazatel na funkci, která je vhodná pro použití jako `unexpected_handler`.  
  
```
typedef void (*unexpected_handler)();
```  
  
### <a name="example"></a>Příklad  
  V tématu [set_unexpected –](../standard-library/exception-functions.md#set_unexpected) příklad použití `unexpected_handler`.  
  
## <a name="see-also"></a>Viz také  
 [\<Výjimka >](../standard-library/exception.md)



