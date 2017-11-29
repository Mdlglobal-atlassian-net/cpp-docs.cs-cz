---
title: CRowset::UpdateAll | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset::UpdateAll
- ATL.CRowset.UpdateAll
- CRowset<TAccessor>.UpdateAll
- ATL.CRowset<TAccessor>.UpdateAll
- UpdateAll
- CRowset.UpdateAll
- ATL::CRowset<TAccessor>::UpdateAll
- CRowset<TAccessor>::UpdateAll
- ATL::CRowset::UpdateAll
dev_langs: C++
helpviewer_keywords: UpdateAll method
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5842fb52d2dae255186bb3e56da6e5a6744e1f0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetupdateall"></a>CRowset::UpdateAll
Odesílá všechny neuložené změny provedené na všechny řádky od posledního načtení nebo **aktualizace** volání na něm.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT UpdateAll(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcRows`  
 [out] Ukazatel do umístění, kde `UpdateAll` vrátí počet řádků, které se pokusil aktualizovat, pokud je to nutné.  
  
 `pphRow`  
 [out] Ukazatel na paměti, ve kterém `UpdateAll` vrátí popisovač řádku se pokusil aktualizovat. Žádná obslužná rutina je vrácena v případě `pphRow` má hodnotu null.  
  
 `ppStatus`  
 [out] Ukazatel do umístění, kde **aktualizace** vrátí hodnotu stavový řádek. Pokud je vrácen žádný stav `ppStatus` má hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Odesílá všechny neuložené změny provedené na všechny řádky, protože tyto řádky byly posledního načtení nebo aktualizovat pomocí [aktualizace](../../data/oledb/crowset-update.md) nebo `UpdateAll`. `UpdateAll`aktualizuje každý řádek, která byla změněna, bez ohledu na to, jestli máte popisovač pro ně (viz `pphRow`) nebo ne.  
  
 Pokud jste použili například **vložit** vložit pět řádky v sadě řádků, může buď volání **aktualizace** pětkrát nebo volání `UpdateAll` jednou je všechny aktualizovat.  
  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetUpdate`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetUpdate** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)