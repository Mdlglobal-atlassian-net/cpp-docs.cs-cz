---
title: "enable_shared_from_this – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- memory/std::enable_shared_from_this
dev_langs:
- C++
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3820d060d0c1255253857168383188fdfe0d22
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this – třída
Pomáhá generovat `shared_ptr`.  
  
## <a name="syntax"></a>Syntaxe  
```    
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
}; 
``` 
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ řízené sdílené ukazatele.  
  
## <a name="remarks"></a>Poznámky  
 Odvozené objekty z `enable_shared_from_this` můžete použít `shared_from_this` metody v členské funkce vytvořit [shared_ptr](../standard-library/shared-ptr-class.md) vlastníky instance, které sdílejí vlastnictví s existujícím `shared_ptr` vlastníky. Jinak, pokud vytvoříte novou `shared_ptr` pomocí `this`, se liší od stávající `shared_ptr` vlastníků, což může vést k neplatné odkazy nebo způsobit objekt, který má být odstraněn více než jednou.  
  
 To pomáhá zabránit náhodnému zneužití jsou chráněné konstruktory, destruktor a operátor přiřazení. Typ argumentu šablony `Ty` musí být typu odvozené třídy.  
  
 Příklad použití, naleznete v části [enable_shared_from_this::shared_from_this](#shared_from_this).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<paměti >  
  
 **Namespace:** – std  
  
##  <a name="shared_from_this"></a>  enable_shared_from_this::shared_from_this  
 Generuje `shared_ptr` , vlastnictví instance sdílí s existujícím `shared_ptr` vlastníky.  
  
```  
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud odvozujete objekty z `enable_shared_from_this` základní třídy, `shared_from_this` šablony členské funkce vrátí [shared_ptr – třída](../standard-library/shared-ptr-class.md) objekt, který sdílí vlastnictví této instance s existující `shared_ptr` vlastníky. Jinak, pokud vytvoříte novou `shared_ptr` z `this`, se liší od stávající `shared_ptr` vlastníků, což může vést k neplatné odkazy nebo způsobit objekt, který má být odstraněn více než jednou. Toto chování je definován při volání `shared_from_this` na instanci, která již není vlastníkem `shared_ptr` objektu.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std_memory_shared_from_this.cpp   
// compile with: /EHsc   
#include <memory>  
#include <iostream>  
  
using namespace std;  
  
struct base : public std::enable_shared_from_this<base>  
{  
    int val;    
    shared_ptr<base> share_more()  
    {  
        return shared_from_this();  
    }  
};  
  
int main()  
{  
    auto sp1 = make_shared<base>();  
    auto sp2 = sp1->share_more();  
  
    sp1->val = 3;  
    cout << "sp2->val == " << sp2->val << endl;    
    return 0;  
}   
```  
  
```Output  
sp2->val == 3  
```  
  
## <a name="see-also"></a>Viz také  
 [enable_shared_from_this::shared_from_this](#shared_from_this)   
 [shared_ptr – třída](../standard-library/shared-ptr-class.md)