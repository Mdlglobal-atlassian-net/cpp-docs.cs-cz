---
title: Concurrency::Direct3D – Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
dev_langs:
- C++
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9516e3f89d393405a5f71af569a50e46e381d579
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d – obor názvů
`direct3d` Obor názvů obsahuje funkce, které podporují D3D interoperability. Ji umožňuje bezproblémové použít D3D prostředků pro výpočet v kódu AMP a také umožňuje používat prostředky vytvořené v AMP v kódu D3D bez vytvoření redundantní kopie zprostředkující. Můžete přírůstkově urychlit náročné části výpočetní DirectX aplikací s použitím C++ AMP a použít rozhraní API D3D na dat vytvářených z AMP výpočty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[scoped_d3d_access_lock – třída](scoped-d3d-access-lock-class.md)|RAII obálku pro zámek D3D přístup na `accelerator_view` objektu.|  
  
### <a name="structures"></a>Struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t – struktura](adopt-d3d-access-lock-t-structure.md)|Typ značky k označení zámek přístup D3D by měla být přijata spíše než získali.|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[Abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Vrátí absolutní hodnotu argumentu|  
|[svorka](concurrency-direct3d-namespace-functions-amp.md#clamp)|Přetíženo. Svorky _X pro zadaný rozsah _min – a _maximální|  
|[countbits –](concurrency-direct3d-namespace-functions-amp.md#countbits)|Spočítá počet sadu bitů _X|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Vytvoří [accelerator_view – třída](accelerator-view-class.md) z ukazatel na rozhraní Direct3D – zařízení|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Získá zámek na accelerator_view za účelem provádění bezpečně D3D operací s prostředky, které jsou sdíleny s accelerator_view|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Pokuste se získat zámek D3D přístup accelerator_view bez blokování.|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Uvolní zámek D3D přístup na danou accelerator_view.|  
|[firstbithigh –](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Získá umístění první sada bit v _X, od nejvyšší pořadí bitů a práci dolů|  
|[firstbitlow –](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Získá umístění první sada bit v _X, od nejnižší bitem a práci směrem nahoru|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Získáte rozhraní vyrovnávací paměti D3D základní pole.|  
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Porovná dvě hodnoty, vrátí hodnotu, která je větší.|  
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Porovná dvě hodnoty, vrátí hodnotu, která je menší.|  
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Vrátí logický příznak indikující, pokud je pro zadaný accelerator_view zakázané časový limit.|  
|[MAD –](concurrency-direct3d-namespace-functions-amp.md#mad)|Přetíženo. Provede operaci aritmetické násobení nebo přidat na tři argumenty: _X * _Y + _Z –|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Vytvořte pole z rozhraní ukazatel D3D vyrovnávací paměti.|  
|[šumu](concurrency-direct3d-namespace-functions-amp.md#noise)|Generuje náhodná hodnota pomocí algoritmu šumu Perlin|  
|[radiánech](concurrency-direct3d-namespace-functions-amp.md#radians)|Převede _X z stupňů radiánech|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Vypočítá rychlé, přibližnou vzájemné argumentu|  
|[reversebits –](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Obrátí pořadí bity v _X|  
|[saturate –](concurrency-direct3d-namespace-functions-amp.md#saturate)|Svorky _X v rozsahu 0 až 1|  
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Přetíženo. Vrátí znaménko argumentu|  
|[smoothstep –](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Vrátí smooth interpolace Hermite mezi 0 a 1, pokud _X je v rozsahu [_min –, _maximální].|  
|[Krok](concurrency-direct3d-namespace-functions-amp.md#step)|Porovná dvě hodnoty, vrácení 0 nebo 1 na základě toho, která hodnota větší|  
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|Porovná dvě nepodepsané hodnoty, vrátí hodnotu, která je větší.|  
|[umin –](concurrency-direct3d-namespace-functions-amp.md#umin)|Porovná dvě nepodepsané hodnoty, vrátí hodnotu, která je menší.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
