---
title: Concurrency::Direct3D – Namespace | Dokumentace Microsoftu
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
ms.openlocfilehash: e95a0cb4b2dc8dfae7667a147dc2912cd7922c3d
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207689"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d – obor názvů
`direct3d` Obor názvů poskytuje funkce podporující spolupráci rozhraní D3D. To umožňuje bezproblémové použití zdrojů rozhraní D3D pro výpočet kódu Knihovny i využití zdrojů vytvořených v knihovně AMP v kódu D3D bez nutnosti vytvářet nadbytečné pomocné kopie. Postupně zrychlí provádění výpočetně náročných oddílů DirectX aplikace s použitím jazyka C++ AMP a použít rozhraní D3D API nad daty vytvořenými výpočty AMP.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[scoped_d3d_access_lock – třída](scoped-d3d-access-lock-class.md)|Obálka RAII pro uzamčení přístupu D3D na `accelerator_view` objektu.|  
  
### <a name="structures"></a>Struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t – struktura](adopt-d3d-access-lock-t-structure.md)|Typ tagu pro označení uzamčení přístupu D3D by měla být přijata spíše než získána.|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[Abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Vrátí absolutní hodnotu argumentu|  
|[Stažení](concurrency-direct3d-namespace-functions-amp.md#clamp)|Přetíženo. Omezí hodnotu proměnné _X na zadaném rozsahu _min do _max|  
|[countbits –](concurrency-direct3d-namespace-functions-amp.md#countbits)|Spočítá počet nastavených bitů v proměnné _X|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Vytvoří [accelerator_view – třída](accelerator-view-class.md) z ukazatele na rozhraní zařízení Direct3D|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Získá zámek na accelerator_view pro účely bezpečného provádění operací D3D na prostředcích sdílených s accelerator_view|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Pokus o získání zámku přístupu D3D na accelerator_view bez blokování.|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Uvolněte zámek přístupu D3D na daný objekt accelerator_view.|  
|[firstbithigh –](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Zjistí umístění prvního nastaveného bitu v _X, počínaje bitem nejvyšší a funguje směrem dolů|  
|[firstbitlow –](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Zjistí umístění prvního nastaveného bitu v _X, počínaje bitem nejnižší a funguje směrem nahoru|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Získejte rozhraní vyrovnávací paměti rozhraní D3D podkládajícího pole.|  
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Porovná dvě hodnoty a vrátí hodnotu, která je větší.|  
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Porovná dvě hodnoty a vrátí hodnotu, která je menší.|  
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Vrátí příznak logické hodnoty označující, pokud vypršení časového limitu je zakázáno pro zadaný accelerator_view.|  
|[MAD –](concurrency-direct3d-namespace-functions-amp.md#mad)|Přetíženo. Provede operaci aritmetické násobení/sčítání nad třemi argumenty: _X \* _Y + _Z|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Vytvoří pole z ukazatele na rozhraní vyrovnávací paměti rozhraní D3D.|  
|[šumu](concurrency-direct3d-namespace-functions-amp.md#noise)|Vygeneruje náhodnou hodnotu pomocí algoritmu Perlinova šumu.|  
|[RADIANS](concurrency-direct3d-namespace-functions-amp.md#radians)|Převede proměnnou _X ze stupňů na radiány.|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Vypočítá rychlou, přibližnou převrácenou hodnotu argumentu|  
|[reversebits –](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Obrátí pořadí bitů v proměnné _X|  
|[Saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|Omezí hodnotu proměnné _X z rozsahu 0 až 1|  
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Přetíženo. Vrátí znaménko argumentu|  
|[smoothstep –](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Vrátí smooth Hermitovu interpolaci mezi 0 a 1, pokud _X je v rozsahu [_Min, _Max].|  
|[Krok](concurrency-direct3d-namespace-functions-amp.md#step)|Porovná dvě hodnoty a vrátí hodnotu 0 nebo 1 podle toho, která hodnota je větší|  
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|Porovná dvě nepodepsané hodnoty a vrátí hodnotu, která je větší.|  
|[umin –](concurrency-direct3d-namespace-functions-amp.md#umin)|Porovná dvě nepodepsané hodnoty a vrátí hodnotu, která je menší.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
