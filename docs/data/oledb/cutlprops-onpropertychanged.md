---
title: CUtlProps::OnPropertyChanged | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
dev_langs: C++
helpviewer_keywords: OnPropertyChanged method
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b517bfe6ef3cc93b6edf647d137491ef78c0f716
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cutlpropsonpropertychanged"></a>CUtlProps::OnPropertyChanged
Volá se po nastavení vlastností pro zpracování zřetězené vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      virtual HRESULT OnPropertyChanged(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
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