## Follow theese instructions to install vRP_DrugsExtended.
## Only install this way if you already have done custom stuff with vrp/cfg/items, vrp/cfg/item_transformers, vrp/cfg/groups.lua

1. Go to vrp/cfg/groups.lua and add this code BETWEEN two other jobs:
 ["Drug Dealer"] = {
    _config = { gtype = "job",
	    onspawn = function(player) vRPclient.notify(player,{"You are a Drug Dealer."}) end
	  },
	"drugseller.market",
	"vrpdrugs.extendedsell"
  },
  ["Street Pusher"] = {
    _config = { gtype = "job",
	    onspawn = function(player) vRPclient.notify(player,{"You are a Street Pusher."}) end
	  },
    "mission.drugseller.weed",
    "drugseller.market",
    "harvest.weed"
  },
  ["Drug Mixer"] = {
    _config = { gtype = "job",
	    onspawn = function(player) vRPclient.notify(player,{"You are a drug mixer."}) end
	  },
    "vrpdrugs.extendedmix"
  },
  ["Drug Grower"] = {
    _config = { gtype = "job",
	    onspawn = function(player) vRPclient.notify(player,{"You are a drug grower."}) end
	  },
	"harvest.weed"
  },

2. Save that file
3. Go to vrp/cfg/items.lua and add this code BETWEEN two other items:
  ["lysergicacidamide"] = {"Lysergicacidamide", "Some acid.", nil, 0.05}, -- no choices
  ["cocoleaves"] = {"Coco Leaves", "Some Coco Leaves.", nil, 0.15}, -- no choices
  ["cleancoke"] = {"Clean Cocaine", "Some Pure Cocaine.", nil, 0.10}, -- no choices'
  ["cleanlsd"] = {"Clean LSD", "Some Pure LSD.", nil, 0.10}, -- no choices
  
  4. Save that file
  5. Go to vrp/cfg/item_transformers.lua and add this code BETWEEN two other items:
    ["Lysergicacidamide"] = {
    def = {
      name="Lysergicacidamide", -- menu name
      permissions = {"harvest.weed"}, -- you can add permissions
      r=0,g=200,b=0, -- color
      max_units=100000,
      units_per_minute=100000,
      x=0,y=0,z=0, -- pos
      radius=5, height=1.5, -- area
      recipes = {
        ["Harvest"] = { -- action name
          description="Harvest some drugs.", -- action description
          in_money=0, -- money taken per unit
          out_money=0, -- money earned per unit
          reagents={}, -- items taken per unit
          products={ -- items given per unit
      			["lysergicacidamide"] = 1
          }
        }
      }
    },
    positions = {
      {-574.02404785156,286.56427001953,79.176689147949}
    }
  },
  ["Coco Leaves"] = {
    def = {
      name="Coco Leaves", -- menu name
      permissions = {"harvest.weed"}, -- you can add permissions
      r=0,g=200,b=0, -- color
      max_units=100000,
      units_per_minute=100000,
      x=0,y=0,z=0, -- pos
      radius=5, height=1.5, -- area
      recipes = {
        ["Harvest"] = { -- action name
          description="Harvest some drugs.", -- action description
          in_money=0, -- money taken per unit
          out_money=0, -- money earned per unit
          reagents={}, -- items taken per unit
          products={ -- items given per unit
      			["cocoleaves"] = 1
          }
        }
      }
    },
    positions = {
      {-1113.3039550781,4903.4130859375,218.59548950195}
    }
  },
  ["Mix Cocaine"] = {
    def = {
      name="Mix Benzoilmetilecgonina and Coco Leaves", -- menu name
      permissions = {"vrpdrugs.extendedmix"}, -- you can add permissions
      r=0,g=200,b=0, -- color
      max_units=100000,
      units_per_minute=100000,
      x=0,y=0,z=0, -- pos
      radius=5, height=1.5, -- area
      recipes = {
        ["Mix"] = { -- action name
          description="Mixing your ingredients.", -- action description
          in_money=0, -- money taken per unit
          out_money=0, -- money earned per unit
          reagents={
            ["cocoleaves","benzoilmetilecgonina"] = 1
           }, -- items taken per unit
          products={ -- items given per unit
      			["cleancoke"] = 3
          }
        }
      }
    },
    positions = {
      {990.45965576172,-2149.2961425781,30.20534324646}
    }
  },
    ["Mix LSD"] = {
      def = {
        name="Mix Lysergicacidamide and Harness", -- menu name
        permissions = {"vrpdrugs.extendedmix"}, -- you can add permissions
        r=0,g=200,b=0, -- color
        max_units=100000,
        units_per_minute=100000,
        x=0,y=0,z=0, -- pos
        radius=5, height=1.5, -- area
        recipes = {
          ["Mix"] = { -- action name
            description="Mixing your ingredients.", -- action description
            in_money=0, -- money taken per unit
            out_money=0, -- money earned per unit
            reagents={
              ["harness"] = 1,
              ["lysergicacidamide"] = 1
            }, -- items taken per unit
            products={ -- items given per unit
              ["cleanlsd"] = 3
            }
          }
        }
      },
    positions = {
      {-431.19342041016,-23.734369277954,46.228424072266}
    }
  },
  ["Sell Weed"] = {
    def = {
      name="Sell Weed", -- menu name
      permissions = {"vrpdrugs.extendedsell"}, -- you can add permissions
      r=0,g=200,b=0, -- color
      max_units=100000,
      units_per_minute=100000,
      x=0,y=0,z=0, -- pos
      radius=5, height=1.5, -- area
      recipes = {
        ["Sell"] = { -- action name
          description="Selling your drugs.", -- action description
          in_money=0, -- money taken per unit
          out_money=0, -- money earned per unit
          reagents={
            ["weed"] = 1
          }, -- items taken per unit
          products={ -- items given per unit
            ["dirty_money"] = 900 + math.random(50,100)
          }
        }
      }
    },
  positions = {
    {1969.5650634766,3814.6298828125,33.428737640381}
  }
},
["Sell Cocaine"] = {
  def = {
    name="Sell Some Pure Cocaine", -- menu name
    permissions = {"vrpdrugs.extendedsell"}, -- you can add permissions
    r=0,g=200,b=0, -- color
    max_units=100000,
    units_per_minute=100000,
    x=0,y=0,z=0, -- pos
    radius=5, height=1.5, -- area
    recipes = {
      ["Sell"] = { -- action name
        description="Selling your drugs.", -- action description
        in_money=0, -- money taken per unit
        out_money=0, -- money earned per unit
        reagents={
          ["cleancoke"] = 1
        }, -- items taken per unit
        products={ -- items given per unit
          ["dirty_money"] = 900 + math.random(300,500)
        }
      }
    }
  },
positions = {
  {85.907402038574,-1959.8189697266,21.121690750122}
 }
},
["Sell LSD"] = {
  def = {
    name="Sell Some Clean LSD", -- menu name
    permissions = {"vrpdrugs.extendedsell"}, -- you can add permissions
    r=0,g=200,b=0, -- color
    max_units=100000,
    units_per_minute=100000,
    x=0,y=0,z=0, -- pos
    radius=5, height=1.5, -- area
    recipes = {
      ["Sell"] = { -- action name
        description="Selling your drugs.", -- action description
        in_money=0, -- money taken per unit
        out_money=0, -- money earned per unit
        reagents={
          ["cleanlsd"] = 1
        }, -- items taken per unit
        products={ -- items given per unit
          ["dirty_money"] = 900 + math.random(150,300)
        }
      }
    }
  },
positions = {
  {1372.8470458984,-555.65594482422,74.685569763184}
 }
},

6. Save that file
7. OPTIONAL - IF YOU WANT MARKERS FOR THE DIFFRENT LOCATIONS THEN DO STEP 8 & 9, IF YOU DON'T WANT MARKERS (NOT BLIPS, MARKERS) THEN DO STEP 8 & 9
8. Open vrp/cfg/blip_markers.lua
9. Replace the markers with theese::
{743.19586181641,3895.3967285156,30.556676864624,1.5,1.5,1.5,204,204,0,150,35}, -- Place where to get the fish from.
{1508.8854980469,3908.5732421875,30.031631,1,1,0.8,204,204,0,150,35}, -- Place to get the boat from (marked on the ground)
{-342.75030517578,6098.2495117188,30.318670272827,1,1,0.8,204,204,0,150,35}, -- Place to get the illegal weapons from
{2213.0520019531,5577.5981445313,52.795757293701,1,1,0.8,204,204,0,150,35}, -- Place to harvest Medical Weed
{-261.40533447266,-965.15747070313,30.224115371704,1,1,0.8,204,204,0,150,35}, -- Place to get Drivers License
{805.77130126953,1078.0639648438,27.55744934082,1,1,0.8,204,204,0,150,35}, -- Place to get Trash
{439.57083129883,-995.072265625,29.689596176147,1,1,0.8,204,204,0,150,35}, -- Mission Row Police Report
{1851.6605224609,3690.6713867188,33.267044067383,1,1,0.8,204,204,0,150,35}, -- Sandy Shores Police Report
{-449.43395996094,6010.796875,30.716377258301,1,1,0.8,204,204,0,150,35}, -- Paleto Police Report
{-272.08700561523,27.639623641968,53.752536773682,1,1,0.8,204,204,0,150,35}, -- Medical Report
{465.04064941406,3569.1174316406,32.238555908203,1,1,0.8,204,204,0,150,35}, -- Medical Report
{-1145.8566894531,4939.5083007813,221.2686920166,1,1,0.8,204,204,0,150,35}, -- Medical Report
{1618.9204101563,3227.7058105469,39.411529541016,1,1,0.8,204,204,0,150,35}, -- Cargo Collection
{807.07354736328,-1077.0104980469,27.621067047119,1,1,0.8,204,204,0,150,35}, -- Trash
{-574.02404785156,286.56427001953,79.176689147949,1,1,0.8,204,204,0,150,35}, -- Lysergicacidamide
{-1113.3039550781,4903.4130859375,218.59548950195,1,1,0.8,204,204,0,150,35}, -- Coco Leaves
{990.45965576172,-2149.2961425781,30.20534324646,1,1,0.8,204,204,0,150,35}, -- Cocaine Mixer
{-431.19342041016,-23.734369277954,46.228424072266,1,1,0.8,204,204,0,150,35}, -- LSD Mixer
{-60.876930236816,-1218.3879394531,28.701858520508,1,1,0.8,204,204,0,150,35}, -- Sell Weed
{85.907402038574,-1959.8189697266,21.121690750122,1,1,0.8,204,204,0,150,35}, -- Sell Cocaine
{-1378.4660644531,-622.89190673828,31.29504776001,1,1,0.8,204,204,0,150,35}, -- Sell LSD
{1992.5993652344,3044.1806640625,47.215068817139,1,1,0.8,204,204,0,150,35}, -- Harvest Harness
{-631.00543212891,-229.42568969727,38.057052612305,1,1,0.8,204,204,0,150,35} -- Harvest benzoilmetilecgonina

10. Now you have installed vRP_DrugsExtended :)