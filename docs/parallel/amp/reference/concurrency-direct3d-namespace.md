---
title: Concurrency::direct3d – obor názvů
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: e1374acbd7061afaba372100cf6e69d9d717da8a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127030"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d – obor názvů

Obor názvů `direct3d` poskytuje funkce, které podporují interoperabilitu rozhraní D3D. Umožňuje použít prostředky D3D k výpočtům v kódu AMP. V kódu D3D taky umožňuje používat prostředky vytvořené v AMP v kódu, aniž byste museli vytvářet nadbytečné mezilehlé kopie. Pomocí C++ amp můžete postupně zrychlit oddíly náročné na výpočetní výkon aplikací rozhraní DirectX a použít rozhraní D3D API pro data vytvořená pomocí výpočtů amp.

## <a name="syntax"></a>Syntaxe

```cpp
namespace direct3d;
```

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[scoped_d3d_access_lock – třída](scoped-d3d-access-lock-class.md)|Obálka RAII pro zámek přístupu D3D u objektu `accelerator_view`.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[adopt_d3d_access_lock_t – struktura](adopt-d3d-access-lock-t-structure.md)|Typ značky označující, že by měl být přijat zámek přístupu D3D místo získání.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[ABS](concurrency-direct3d-namespace-functions-amp.md#abs)|Vrátí absolutní hodnotu argumentu.|
|[Clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|Přetíženo. Svorky _X do zadaného _Min a rozsahu _Max|
|[countbits –](concurrency-direct3d-namespace-functions-amp.md#countbits)|Spočítá počet sad bitů v _X.|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Vytvoří [třídu accelerator_view](accelerator-view-class.md) z ukazatele na rozhraní zařízení Direct3D.|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Získá zámek na accelerator_view pro bezpečné provádění operací D3D na prostředcích sdílených s accelerator_view|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Došlo k pokusu o získání zámku přístupu D3D na accelerator_view bez blokování.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Uvolněte zámek přístupu D3D na daném accelerator_view.|
|[firstbithigh –](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Získá umístění prvního nastaveného bitu v _X počínaje nejvyšším bitem pořadí a prací směrem dolů.|
|[firstbitlow –](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Získá umístění prvního nastaveného bitu v _X počínaje nejnižším bitem pořadí a spolupracuje nahoru.|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Získá rozhraní vyrovnávací paměti rozhraní D3D, které je podkladové.|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Porovná dvě hodnoty a vrátí hodnotu, která je větší.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Porovná dvě hodnoty a vrátí hodnotu, která je menší.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Vrátí logický příznak označující, zda je časový limit pro zadaný accelerator_view zakázán.|
|[Mad –](concurrency-direct3d-namespace-functions-amp.md#mad)|Přetíženo. Provede aritmetickou operaci násobení nebo přidání na třech argumentech: _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Vytvoří pole z ukazatele na rozhraní vyrovnávací paměti rozhraní D3D.|
|[neobsažných](concurrency-direct3d-namespace-functions-amp.md#noise)|Generuje náhodnou hodnotu pomocí algoritmu Perlin šumu.|
|[rad](concurrency-direct3d-namespace-functions-amp.md#radians)|Převede _X ze stupňů na radiány.|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Vypočítá rychlou a přibližnou převrácenou hodnotu argumentu.|
|[reversebits –](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Obrátí pořadí bitů v _X|
|[saturate –](concurrency-direct3d-namespace-functions-amp.md#saturate)|Svorky _X v rozsahu od 0 do 1.|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Přetíženo. Vrátí znaménko argumentu.|
|[smoothstep –](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Vrátí plynulou Hermitovu interpolaci mezi 0 a 1, pokud je _X v rozsahu [_Min, _Max].|
|[Krok](concurrency-direct3d-namespace-functions-amp.md#step)|Porovná dvě hodnoty, vrátí hodnotu 0 nebo 1 podle toho, která hodnota je větší.|
|[společnosti](concurrency-direct3d-namespace-functions-amp.md#umax)|Porovná dvě nepodepsané hodnoty a vrátí hodnotu, která je větší.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Porovná dvě nepodepsané hodnoty a vrátí hodnotu, která je menší.|

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
