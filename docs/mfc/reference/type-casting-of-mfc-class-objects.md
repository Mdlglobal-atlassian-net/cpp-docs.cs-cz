---
title: "Typ přetypování objektů tříd MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc887ad855b00b525c74b66bfc70f2adb3312e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-casting-of-mfc-class-objects"></a>Přetypování objektů tříd MFC
Typ přetypování makra poskytují způsob, jak převést danou ukazatel na ukazatele, který odkazuje na objekt určité třídy, s nebo bez kontroly, zda je právní přetypování.  
  
 Následující tabulka uvádí makry MFC typ přetypování.  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, která přetypování ukazatelů na objekty tříd MFC  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST –](#dynamic_downcast)|Ukazatel na ukazatel na objekt třídy vrhá při kontrole, jestli je právní přetypování.|  
|[STATIC_DOWNCAST –](#static_downcast)|Vrhá ukazatel na objekt z jednu třídu k ukazatel souvisejícího typu. V sestavení ladicí verze, způsobí, že **ASSERT** Pokud objekt se nenachází "druh" typu cíle.|  
  
##  <a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST –  
 Umožňuje snadno přetypovat ukazatel na ukazatel na objekt třídy při kontrole, jestli je právní přetypování.  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>Parametry  
 `class`  
 Název třídy.  
  
 `pointer`  
 Ukazatel na přetypovat na ukazatel na objekt typu `class`.  
  
### <a name="remarks"></a>Poznámky  
 Makro bude přetypovat `pointer` parametr ukazatele na objekt `class` typ parametru.  
  
 Pokud je objekt odkazuje ukazatele "druh" zjištěné třídy makro vrátí odpovídající ukazatele. Pokud není právní přetypování, vrátí makro **NULL**.  
  
##  <a name="static_downcast"></a>STATIC_DOWNCAST –  
 Přetypování *pobject* na ukazatel *class_name* objektu.  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy je převést na.  
  
 *pobject*  
 Má ukazatel na ukazatel na přetypovat *class_name* objektu.  
  
### <a name="remarks"></a>Poznámky  
 *pobject* musí být buď **NULL**, nebo přejděte na objekt třídy, které je odvozeno přímo nebo nepřímo, z *class_name*. V sestavení vaší aplikace pomocí **_DEBUG –** – symbol preprocesoru definované, bude makro **ASSERT** Pokud *pobject* není **NULL**, nebo odkazuje na objekt, který není "druh" Třída zadaná v *class_name* parametr (viz [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). V jinou hodnotu než **_DEBUG –** sestavení, makro provede přetypování bez kontroly typu.  
  
 Třída zadaná v *class_name* parametr musí být odvozen od `CObject` a musí používat `DECLARE_DYNAMIC` a `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE`, nebo `DECLARE_SERIAL` a `IMPLEMENT_SERIAL`makra, jak je popsáno v článku [CObject – třída: odvození třídy z objektu CObject](../../mfc/deriving-a-class-from-cobject.md).  
  
 Například může přetypovat ukazatel na `CMyDoc`, volané `pMyDoc`, na ukazatel na **CDocument** pomocí výrazu:  
  
 [!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 Pokud `pMyDoc` neukazuje na objekt odvozené přímo nebo nepřímo z **CDocument**, bude makro **ASSERT**.  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
