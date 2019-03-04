---
title: Volání skriptů (ATL)
ms.date: 11/04/2016
f1_keywords:
- StringRegister
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
ms.openlocfilehash: 6a604b6105612ad89a12026121c464028535d7df
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287814"
---
# <a name="invoking-scripts"></a>Volání skriptů

[Použití nahraditelných parametrů (preprocesor The registrátoru)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) popisuje nahrazení mapy a uvádí způsob doménový Registrátor **AddReplacement**. Doménový Registrátor má osm jiné metody specifické pro skriptování a všechny jsou popsány v následující tabulce.

|Metoda|Syntaxe/popis|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);**<br /><br /> Zaregistruje skript obsažené v modulu prostředků. *resFileName* označuje cestu UNC do modulu samotný. *nID* a *szType* obsahovat ID a typ prostředku v uvedeném pořadí.|
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);**<br /><br /> Zruší registraci skript obsažené v modulu prostředků. *resFileName* označuje cestu UNC do modulu samotný. *nID* a *szType* obsahovat ID a typ prostředku v uvedeném pořadí.|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);**<br /><br /> Zaregistruje skript obsažené v modulu prostředků. *resFileName* označuje cestu UNC do modulu samotný. *szID* a *szType* obsahují řetězec identifikátoru a typ prostředku v uvedeném pořadí.|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType` **);**<br /><br /> Zruší registraci skript obsažené v modulu prostředků. *resFileName* označuje cestu UNC do modulu samotný. *szID* a *szType* obsahují řetězec identifikátoru a typ prostředku v uvedeném pořadí.|
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);**<br /><br /> Zaregistruje v souboru skriptu. *Název souboru* je cesta UNC k souboru, který obsahuje (nebo) skript prostředků.|
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);**<br /><br /> Zruší registraci skriptu do souboru. *Název souboru* je cesta UNC k souboru, který obsahuje (nebo) skript prostředků.|
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***data***);**<br /><br /> Zaregistruje skript v řetězci. *data* obsahuje samotný skript.|
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***data***);**<br /><br /> Zruší registraci skript v řetězci. *data* obsahuje samotný skript.|

**ResourceRegisterSz** a **ResourceUnregisterSz**, jsou podobné **ResourceRegister** a **ResourceUnregister**, ale umožňují zadat řetězec identifikátor.

Metody **FileRegister** a **FileUnregister** jsou užitečné, pokud nechcete, aby se skript v prostředku nebo pokud chcete skript ve vlastním souboru. Metody **StringRegister** a **StringUnregister** souboru .rgs k uložení v řetězci dynamicky přidělené povolených aplikací.

## <a name="see-also"></a>Viz také:

[Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)
