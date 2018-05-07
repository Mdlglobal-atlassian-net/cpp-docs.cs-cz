---
title: CUtlProps::OnPropertyChanged | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
dev_langs:
- C++
helpviewer_keywords:
- OnPropertyChanged method
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c9b52949db714206b6118000d004c6248b7d6235
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cutlpropsonpropertychanged"></a>CUtlProps::OnPropertyChanged
Volá se po nastavení vlastností pro zpracování zřetězené vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iCurSet`  
 Index v poli sada vlastností; nula, pokud je sada pouze jednu vlastnost.  
  
 `pDBProp`  
 ID vlastnosti a nová hodnota v [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) struktury.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`. Vrátí výchozí hodnota je `S_OK`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete zpracovat zřetězené vlastnosti, jako je například záložky nebo aktualizace, které jsou závislé na jiné vlastnosti na hodnotu, jejichž hodnoty by měly přepsat tuto funkci.  
  
## <a name="example"></a>Příklad  
 V této funkci uživatel získá Identifikátor vlastnosti z `DBPROP*` parametr. Nyní je možné k porovnání ID proti vlastnost, která má řetězu. Pokud je vlastnost nalezena, `SetProperties` je volán s vlastnost, která se nastaví ve spojení s jiných vlastností. V tomto případě, pokud jeden získá `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, nebo `DBPROP_ORDEREDBOOKMARKS` vlastnost jedno nastaveno `DBPROP_BOOKMARKS` vlastnost.  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CUtlProps – třída](../../data/oledb/cutlprops-class.md)