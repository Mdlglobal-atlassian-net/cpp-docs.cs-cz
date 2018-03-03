---
title: "Vyvolání skripty (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StringRegister
dev_langs:
- C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cbf969f601bd90e84bf0ee15ae2ea3dcb392610
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="invoking-scripts"></a>Vyvolání skripty
[Nahraditelné parametry (registrátora Preprocessor) pomocí](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) popisuje nahrazení mapy a uvádí metodu registrátora **AddReplacement**. Registrátora má osm jiné metody specifické pro skriptování a všechny jsou popsané v následující tabulce.  
  
|Metoda|Syntaxe nebo popis|  
|------------|-------------------------|  
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Zaregistruje obsažené v prostředku modulu skriptu. *resFileName* Určuje cestu UNC do modulu sám sebe. `nID`a `szType` obsahovat ID a typ prostředku v uvedeném pořadí.|  
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Zruší registraci obsažené v prostředku modulu skriptu. *resFileName* Určuje cestu UNC do modulu sám sebe. `nID`a `szType` obsahovat ID a typ prostředku v uvedeném pořadí.|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);** <br /><br /> Zaregistruje obsažené v prostředku modulu skriptu. *resFileName* Určuje cestu UNC do modulu sám sebe. *szID* a `szType` obsahovat řetězec identifikátoru a typ prostředku v uvedeném pořadí.|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);** <br /><br /> Zruší registraci obsažené v prostředku modulu skriptu. *resFileName* Určuje cestu UNC do modulu sám sebe. *szID* a `szType` obsahovat řetězec identifikátoru a typ prostředku v uvedeném pořadí.|  
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);** <br /><br /> Zaregistruje skript v souboru. *Název souboru* je cesta UNC k souboru, který obsahuje (nebo je) skriptu prostředků.|  
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);** <br /><br /> Zruší registraci skript v souboru. *Název souboru* je cesta UNC k souboru, který obsahuje (nebo je) skriptu prostředků.|  
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***data***);** <br /><br /> Zaregistruje skript v řetězci. *data* obsahuje samotný skript.|  
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***data***);** <br /><br /> Zruší registraci skript v řetězci. *data* obsahuje samotný skript.|  
  
 **ResourceRegisterSz** a **ResourceUnregisterSz**, jsou podobné **ResourceRegister** a **ResourceUnregister**, ale můžete určit identifikátor řetězce.  
  
 Metody **FileRegister** a **FileUnregister** jsou užitečné, pokud nechcete, aby skript v prostředku nebo pokud chcete, aby skript u vlastního souboru. Metody **StringRegister** a **StringUnregister** povolit souboru se neukládají v dynamicky přidělené řetězec.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)

