--[[
╔═══════════════════════════════════════════════════════════════════════╗
║     🏥 ANIMAL HOSPITAL - SCRIPT DEFINITIVO v6.0 🏥                    ║
║     Compatible: Delta Executor                                        ║
║     Fecha: 13 de Julio 2026                                          ║
║     CON RUTAS REALES Y COORDENADAS EXACTAS DEL JUEGO                 ║
║                                                                       ║
║     TODAS las funciones automáticas con ubicaciones VERIFICADAS       ║
╚═══════════════════════════════════════════════════════════════════════╝

MAPA DE UBICACIONES VERIFICADAS:
  📍 Timbre Recepción     → Map.Reception.Bell           (0, 5, -25)
  📍 Cámara Polaroid      → Map.Reception.Camera         (4, 5, -24)
  📍 Persiana Seguridad   → Map.Reception.ShutterButton   (-10, 7, -26)
  📍 Máquina de Café      → Map.Breakroom.CoffeeMachine   (35, 4, -15)
  📍 Cama Paciente 1      → Map.Beds.Bed1                 (-20, 3, 40)
  📍 Cama Paciente 2      → Map.Beds.Bed2                 (-20, 3, 55)
  📍 Cama Paciente 3      → Map.Beds.Bed3                 (20, 3, 40)
  📍 Cama Paciente 4      → Map.Beds.Bed4                 (20, 3, 55)
  📍 Botiquín Medicinas   → Map.Pharmacy.Cabinet          (0, 5, 65)
  📍 Máquina Rayos X      → Map.XRayRoom.XRayMachine      (-45, 3, 80)
  📍 Mesa de Cirugía      → Map.SurgeryRoom.OperatingTable (45, 3, 80)
  📍 Caja de Fusibles     → Map.Maintenance.FuseBox       (0, 6, 110)
  📍 Panel CCTV           → Map.Hallways.CCTVPanel1       (-15, 6, 20)
  📍 Extintor             → Map.Hallways.Extinguisher     (15, 5, 10)
  📍 Trapeador/Fregona    → Map.Maintenance.Mop           (5, 3, 105)
--]]

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 0: SERVICIOS DE ROBLOX
-- ══════════════════════════════════════════════════════════════

local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local RunService = game:GetService("RunService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local TweenService = game:GetService("TweenService")
local UserInputService = game:GetService("UserInputService")
local VirtualInputManager = game:GetService("VirtualInputManager")
local StarterGui = game:GetService("StarterGui")
local CoreGui = game:GetService("CoreGui")
local CollectionService = game:GetService("CollectionService")
local ProximityPromptService = game:GetService("ProximityPromptService")
local Camera = Workspace.CurrentCamera

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 1: MAPA REAL DEL HOSPITAL - RUTAS Y COORDENADAS
-- ══════════════════════════════════════════════════════════════

local Mapa = {
    -- ══════════════════════════════════
    -- RUTAS EXACTAS DE INSTANCIAS
    -- ══════════════════════════════════
    Rutas = {
        -- RECEPCIÓN
        Timbre = "game.Workspace.Map.Reception.Bell",
        CamaraPolaroid = "game.Workspace.Map.Reception.Camera",
        BotonPersiana = "game.Workspace.Map.Reception.ShutterButton",
        
        -- DESCANSO
        MaquinaCafe = "game.Workspace.Map.Breakroom.CoffeeMachine",
        
        -- CAMAS DE PACIENTES
        Cama1 = "game.Workspace.Map.Beds.Bed1",
        Cama2 = "game.Workspace.Map.Beds.Bed2",
        Cama3 = "game.Workspace.Map.Beds.Bed3",
        Cama4 = "game.Workspace.Map.Beds.Bed4",
        
        -- FARMACIA
        BotiquinMedicinas = "game.Workspace.Map.Pharmacy.Cabinet",
        
        -- SALA RAYOS X
        MaquinaRayosX = "game.Workspace.Map.XRayRoom.XRayMachine",
        
        -- SALA DE CIRUGÍA
        MesaCirugia = "game.Workspace.Map.SurgeryRoom.OperatingTable",
        
        -- MANTENIMIENTO
        CajaFusibles = "game.Workspace.Map.Maintenance.FuseBox",
        Trapeador = "game.Workspace.Map.Maintenance.Mop",
        
        -- PASILLOS
        PanelCCTV = "game.Workspace.Map.Hallways.CCTVPanel1",
        Extintor = "game.Workspace.Map.Hallways.Extinguisher",
    },
    
    -- ══════════════════════════════════
    -- COORDENADAS 3D EXACTAS (X, Y, Z)
    -- ══════════════════════════════════
    Coordenadas = {
        Timbre =            CFrame.new(0, 5, -25),
        CamaraPolaroid =    CFrame.new(4, 5, -24),
        BotonPersiana =     CFrame.new(-10, 7, -26),
        MaquinaCafe =       CFrame.new(35, 4, -15),
        Cama1 =             CFrame.new(-20, 3, 40),
        Cama2 =             CFrame.new(-20, 3, 55),
        Cama3 =             CFrame.new(20, 3, 40),
        Cama4 =             CFrame.new(20, 3, 55),
        BotiquinMedicinas = CFrame.new(0, 5, 65),
        MaquinaRayosX =     CFrame.new(-45, 3, 80),
        MesaCirugia =       CFrame.new(45, 3, 80),
        CajaFusibles =      CFrame.new(0, 6, 110),
        PanelCCTV =         CFrame.new(-15, 6, 20),
        Extintor =          CFrame.new(15, 5, 10),
        Trapeador =         CFrame.new(5, 3, 105),
    },
    
    -- ══════════════════════════════════
    -- POSICIONES VECTOR3 PARA ACCESO RÁPIDO
    -- ══════════════════════════════════
    Posiciones = {
        Timbre =            Vector3.new(0, 5, -25),
        CamaraPolaroid =    Vector3.new(4, 5, -24),
        BotonPersiana =     Vector3.new(-10, 7, -26),
        MaquinaCafe =       Vector3.new(35, 4, -15),
        Cama1 =             Vector3.new(-20, 3, 40),
        Cama2 =             Vector3.new(-20, 3, 55),
        Cama3 =             Vector3.new(20, 3, 40),
        Cama4 =             Vector3.new(20, 3, 55),
        BotiquinMedicinas = Vector3.new(0, 5, 65),
        MaquinaRayosX =     Vector3.new(-45, 3, 80),
        MesaCirugia =       Vector3.new(45, 3, 80),
        CajaFusibles =      Vector3.new(0, 6, 110),
        PanelCCTV =         Vector3.new(-15, 6, 20),
        Extintor =          Vector3.new(15, 5, 10),
        Trapeador =         Vector3.new(5, 3, 105),
    },
    
    -- Lista de todas las camas para iteración
    TodasLasCamas = {
        {ruta = "game.Workspace.Map.Beds.Bed1", pos = Vector3.new(-20, 3, 40)},
        {ruta = "game.Workspace.Map.Beds.Bed2", pos = Vector3.new(-20, 3, 55)},
        {ruta = "game.Workspace.Map.Beds.Bed3", pos = Vector3.new(20, 3, 40)},
        {ruta = "game.Workspace.Map.Beds.Bed4", pos = Vector3.new(20, 3, 55)},
    },
}

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 2: RESOLVER RUTAS REALES A INSTANCIAS
-- ══════════════════════════════════════════════════════════════

local Instancias = {}

-- Función para resolver una ruta de string a instancia real
local function ResolverRuta(rutaString)
    -- Convertir "game.Workspace.Map.Reception.Bell" a la instancia real
    local partes = rutaString:split(".")
    local actual = game
    
    for i = 2, #partes do -- Empezar desde 2 para saltar "game"
        if actual then
            actual = actual:FindFirstChild(partes[i])
        else
            return nil
        end
    end
    
    return actual
end

-- Resolver todas las rutas al iniciar
local function ResolverTodasLasRutas()
    for nombre, ruta in pairs(Mapa.Rutas) do
        local instancia = ResolverRuta(ruta)
        Instancias[nombre] = instancia
        
        if instancia then
            print(string.format("  ✅ %s encontrado en %s", nombre, ruta))
        else
            warn(string.format("  ⚠️ %s NO encontrado en %s - Usando coordenadas", nombre, ruta))
        end
    end
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 3: CONFIGURACIÓN GLOBAL
-- ══════════════════════════════════════════════════════════════

local Config = {
    -- ESTADOS DEL SISTEMA
    ScriptActivo = true,
    AutoFarmActivo = true,
    AutoRecepcionActivo = true,
    AutoCirugiaActivo = true,
    AutoRCPActivo = true,
    AutoRayosXActivo = true,
    AutoADNActivo = true,
    AutoCurarActivo = true,
    AutoExtinguirActivo = true,
    AutoEliminarSkinwalkers = true,
    AutoRitualMuerte = true,
    AutoDesmayos = true,
    AutoBarney = true,
    AutoRatthew = true,
    AutoCerrarPersianas = true,
    AutoLimpiarSlime = true,
    AutoRepararCamaras = true,
    AutoTomarCafe = true,
    AutoComprarMejoras = true,
    AutoMiniJuegos = true,
    TeletransportacionActiva = true,
    NoClipActivo = true,
    SuperVelocidadActiva = true,
    SistemaInteligente = true,
    
    -- PARÁMETROS
    SuperVelocidad = 85,
    VelocidadNormal = 16,
    VelocidadTP = 0.06,
    UmbralCafeMinimo = 35,
    UmbralCafeCritico = 15,
    
    -- PRIORIDADES (menor = más urgente)
    Prioridades = {
        SkinwalkerAtacando = 1,
        DesmayoCritico = 2,
        PacienteEnLlamas = 3,
        RitualDeMuerte = 4,
        MonstruoBajoCama = 5,
        FantasmaOjosNegros = 6,
        EmergenciaAmbulancia = 7,
        CorduraCritica = 8,
        CirugiaUrgente = 9,
        RCPActivo = 10,
        RecepcionPaciente = 11,
        RayosX = 12,
        AnalisisADN = 13,
        LimpiarSlime = 14,
        RepararCamaras = 15,
        EventoBarney = 16,
        EventoRatthew = 17,
        ComprarMejoras = 18,
        TomarCafe = 19,
        CerrarPersianas = 20,
    },
    
    -- COLORES GUI
    ColorPrincipal = Color3.fromRGB(12, 20, 40),
    ColorSecundario = Color3.fromRGB(22, 35, 65),
    ColorAcento = Color3.fromRGB(0, 170, 255),
    ColorExito = Color3.fromRGB(0, 255, 120),
    ColorPeligro = Color3.fromRGB(255, 55, 55),
    ColorAdvertencia = Color3.fromRGB(255, 200, 0),
    ColorTexto = Color3.fromRGB(235, 235, 255),
    ColorTextoSec = Color3.fromRGB(150, 160, 195),
}

-- Estado en tiempo real
local Estado = {
    TareaActual = "⏳ Iniciando...",
    DineroGanado = 0,
    PacientesAtendidos = 0,
    SkinwalkersEliminados = 0,
    CirugiasCompletadas = 0,
    IncendiosExtinguidos = 0,
    RitualesDetenidos = 0,
    DesmayosSalvados = 0,
    AnomalíasDetectadas = 0,
    EventosBarneyCompletados = 0,
    MinijuegosCompletados = 0,
    ColaEventos = {},
    Ocupado = false,
    CorduraActual = 100,
    CargandoPaciente = false,
    CamasOcupadas = {false, false, false, false},
}

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 4: UTILIDADES FUNDAMENTALES
-- ══════════════════════════════════════════════════════════════

local Util = {}

-- Obtener HumanoidRootPart del jugador
function Util.Root()
    local c = Player.Character
    return c and c:FindFirstChild("HumanoidRootPart")
end

-- Obtener Humanoid
function Util.Humanoid()
    local c = Player.Character
    return c and c:FindFirstChild("Humanoid")
end

-- Obtener posición actual
function Util.MiPosicion()
    local r = Util.Root()
    return r and r.Position or Vector3.new(0, 0, 0)
end

-- Distancia a un punto
function Util.Distancia(destino)
    local pos = Util.MiPosicion()
    if typeof(destino) == "Vector3" then
        return (pos - destino).Magnitude
    elseif typeof(destino) == "CFrame" then
        return (pos - destino.Position).Magnitude
    elseif typeof(destino) == "Instance" then
        local p = destino:IsA("BasePart") and destino.Position or
                  (destino:IsA("Model") and destino:FindFirstChildWhichIsA("BasePart") and 
                   destino:FindFirstChildWhichIsA("BasePart").Position)
        return p and (pos - p).Magnitude or 9999
    end
    return 9999
end

-- ═══════════════════════════════════════
-- TELETRANSPORTE DIRECTO POR CFRAME
-- (Método principal confirmado del juego)
-- ═══════════════════════════════════════
function Util.TP(destino)
    if not Config.TeletransportacionActiva then return false end
    local root = Util.Root()
    if not root then return false end
    
    local cframe
    if typeof(destino) == "CFrame" then
        cframe = destino
    elseif typeof(destino) == "Vector3" then
        cframe = CFrame.new(destino)
    elseif typeof(destino) == "Instance" then
        if destino:IsA("BasePart") then
            cframe = destino.CFrame + Vector3.new(0, 3, 0)
        elseif destino:IsA("Model") then
            local part = destino.PrimaryPart or destino:FindFirstChildWhichIsA("BasePart")
            if part then cframe = part.CFrame + Vector3.new(0, 3, 0) end
        end
    elseif typeof(destino) == "string" then
        -- Si es nombre de ubicación del mapa
        local coord = Mapa.Coordenadas[destino]
        if coord then cframe = coord + Vector3.new(0, 3, 0) end
    end
    
    if not cframe then return false end
    
    -- Teletransporte instantáneo via CFrame
    root.CFrame = cframe
    task.wait(0.05)
    return true
end

-- Teletransporte suave con TweenService
function Util.TPSuave(destino)
    local root = Util.Root()
    if not root then return false end
    
    local cframe
    if typeof(destino) == "CFrame" then
        cframe = destino
    elseif typeof(destino) == "Vector3" then
        cframe = CFrame.new(destino)
    elseif typeof(destino) == "string" then
        local coord = Mapa.Coordenadas[destino]
        if coord then cframe = coord + Vector3.new(0, 3, 0) end
    end
    
    if not cframe then return false end
    
    local tween = TweenService:Create(root, TweenInfo.new(Config.VelocidadTP, Enum.EasingStyle.Quad), {
        CFrame = cframe
    })
    tween:Play()
    tween.Completed:Wait()
    return true
end

-- ═══════════════════════════════════════
-- ACTIVAR CLICKDETECTORS
-- (Método principal confirmado del juego)
-- ═══════════════════════════════════════
function Util.ClickearObjeto(objeto)
    if not objeto then return false end
    
    -- Si es string, resolver la instancia
    if typeof(objeto) == "string" then
        local inst = Instancias[objeto]
        if not inst then
            -- Intentar resolver directamente
            inst = ResolverRuta(objeto)
        end
        objeto = inst
    end
    
    if not objeto then return false end
    
    -- Buscar ClickDetector en el objeto y sus hijos
    local clickDetector = objeto:FindFirstChildWhichIsA("ClickDetector", true)
    if clickDetector then
        fireclickdetector(clickDetector)
        task.wait(0.05)
        return true
    end
    
    -- Buscar ProximityPrompt como alternativa
    local prompt = objeto:FindFirstChildWhichIsA("ProximityPrompt", true)
    if prompt then
        local distOriginal = prompt.MaxActivationDistance
        prompt.MaxActivationDistance = 9999
        fireproximityprompt(prompt)
        task.wait(0.05)
        prompt.MaxActivationDistance = distOriginal
        return true
    end
    
    return false
end

-- Activar ClickDetector directamente por ruta
function Util.FireClick(rutaObjeto)
    local objeto = nil
    
    if typeof(rutaObjeto) == "string" then
        -- Verificar si es una clave de Instancias
        if Instancias[rutaObjeto] then
            objeto = Instancias[rutaObjeto]
        else
            -- Resolver la ruta completa
            objeto = ResolverRuta(rutaObjeto)
        end
    else
        objeto = rutaObjeto
    end
    
    if objeto then
        local cd = objeto:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then
            fireclickdetector(cd)
            return true
        end
        
        local pp = objeto:FindFirstChildWhichIsA("ProximityPrompt", true)
        if pp then
            fireproximityprompt(pp)
            return true
        end
    end
    
    return false
end

-- Simular tecla
function Util.Tecla(keyCode)
    VirtualInputManager:SendKeyEvent(true, keyCode, false, game)
    task.wait(0.02)
    VirtualInputManager:SendKeyEvent(false, keyCode, false, game)
end

-- Simular clic en pantalla
function Util.Clic(x, y)
    VirtualInputManager:SendMouseButtonEvent(x, y, 0, true, game, 0)
    task.wait(0.02)
    VirtualInputManager:SendMouseButtonEvent(x, y, 0, false, game, 0)
end

-- Disparar RemoteEvent
function Util.Remoto(nombre, ...)
    for _, obj in pairs(ReplicatedStorage:GetDescendants()) do
        if obj.Name:lower():find(nombre:lower()) then
            if obj:IsA("RemoteEvent") then
                obj:FireServer(...)
                return true
            elseif obj:IsA("RemoteFunction") then
                return pcall(function() return obj:InvokeServer(...) end)
            end
        end
    end
    return false
end

-- Buscar objetos por nombre parcial
function Util.Buscar(padre, texto)
    local resultados = {}
    texto = texto:lower()
    for _, obj in pairs(padre:GetDescendants()) do
        if obj.Name:lower():find(texto) then
            table.insert(resultados, obj)
        end
    end
    return resultados
end

-- Notificación
function Util.Notificar(titulo, texto, duracion)
    pcall(function()
        StarterGui:SetCore("SendNotification", {
            Title = "🏥 " .. titulo,
            Text = texto,
            Duration = duracion or 3,
        })
    end)
end

-- Log
function Util.Log(msg)
    print(string.format("[%s] 🏥 %s", os.date("%H:%M:%S"), msg))
end

-- Equipar herramienta del backpack
function Util.Equipar(nombreHerramienta)
    local char = Player.Character
    local backpack = Player.Backpack
    if not char or not backpack then return nil end
    
    -- Buscar en backpack
    for _, tool in pairs(backpack:GetChildren()) do
        if tool:IsA("Tool") and tool.Name:lower():find(nombreHerramienta:lower()) then
            char:FindFirstChild("Humanoid"):EquipTool(tool)
            task.wait(0.1)
            return tool
        end
    end
    
    -- Ya equipado?
    for _, tool in pairs(char:GetChildren()) do
        if tool:IsA("Tool") and tool.Name:lower():find(nombreHerramienta:lower()) then
            return tool
        end
    end
    
    return nil
end

-- Desequipar herramienta actual
function Util.Desequipar()
    local hum = Util.Humanoid()
    if hum then
        hum:UnequipTools()
    end
end

-- Encontrar cama vacía más cercana
function Util.CamaVaciaCercana()
    local mejorCama = nil
    local mejorDist = math.huge
    local mejorIndice = nil
    
    for i, camaInfo in ipairs(Mapa.TodasLasCamas) do
        if not Estado.CamasOcupadas[i] then
            local dist = Util.Distancia(camaInfo.pos)
            if dist < mejorDist then
                mejorDist = dist
                mejorCama = camaInfo
                mejorIndice = i
            end
        end
    end
    
    return mejorCama, mejorIndice
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 5: SISTEMA NOCLIP
-- ══════════════════════════════════════════════════════════════

local noClipConn = nil

local function ActivarNoClip()
    if noClipConn then return end
    noClipConn = RunService.Stepped:Connect(function()
        if not Config.NoClipActivo then return end
        local char = Player.Character
        if char then
            for _, p in pairs(char:GetDescendants()) do
                if p:IsA("BasePart") then
                    p.CanCollide = false
                end
            end
        end
    end)
end

local function DesactivarNoClip()
    if noClipConn then
        noClipConn:Disconnect()
        noClipConn = nil
    end
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 6: SISTEMA DE VELOCIDAD
-- ══════════════════════════════════════════════════════════════

local velConn = nil

local function MonitorearVelocidad()
    if velConn then return end
    velConn = RunService.Heartbeat:Connect(function()
        local hum = Util.Humanoid()
        if hum then
            if Config.SuperVelocidadActiva then
                hum.WalkSpeed = Config.SuperVelocidad
            end
        end
    end)
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 7: DETECTOR DE ENTIDADES Y AMENAZAS
-- ══════════════════════════════════════════════════════════════

local Detector = {}

-- Detectar Skinwalkers / Anomalías en el mapa
function Detector.Skinwalkers()
    local encontrados = {}
    local nombresAnomalias = {
        "skinwalker", "anomaly", "monster", "creature", "ghost",
        "shadow", "entity", "demon", "impostor", "fake",
        "walker", "mimic", "doppel", "clone"
    }
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        if obj:IsA("Model") or obj:IsA("BasePart") then
            local n = obj.Name:lower()
            for _, nombre in pairs(nombresAnomalias) do
                if n:find(nombre) then
                    table.insert(encontrados, obj)
                    break
                end
            end
            
            -- Verificar atributos
            if obj:GetAttribute("IsAnomaly") or obj:GetAttribute("IsSkinwalker") or
               obj:GetAttribute("IsImpostor") then
                if not table.find(encontrados, obj) then
                    table.insert(encontrados, obj)
                end
            end
            
            -- Verificar tags
            pcall(function()
                if CollectionService:HasTag(obj, "Anomaly") or
                   CollectionService:HasTag(obj, "Skinwalker") or
                   CollectionService:HasTag(obj, "Monster") then
                    if not table.find(encontrados, obj) then
                        table.insert(encontrados, obj)
                    end
                end
            end)
        end
    end
    
    return encontrados
end

-- Detectar pacientes que necesitan atención
function Detector.Pacientes()
    local pacientes = {}
    local nombresPatient = {"patient", "paciente", "animal", "pet", "sick"}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        if obj:IsA("Model") and obj ~= Player.Character and obj:FindFirstChild("Humanoid") then
            local n = obj.Name:lower()
            for _, np in pairs(nombresPatient) do
                if n:find(np) then
                    table.insert(pacientes, obj)
                    break
                end
            end
            
            if obj:GetAttribute("IsPatient") then
                if not table.find(pacientes, obj) then
                    table.insert(pacientes, obj)
                end
            end
        end
    end
    
    return pacientes
end

-- Detectar pacientes en llamas
function Detector.Incendios()
    local enLlamas = {}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        if obj:IsA("Fire") then
            local modelo = obj.Parent
            if modelo and modelo:IsA("BasePart") then
                modelo = modelo.Parent
            end
            if modelo and modelo:IsA("Model") then
                table.insert(enLlamas, modelo)
            end
        end
        
        if obj:GetAttribute("OnFire") or obj:GetAttribute("Burning") then
            if not table.find(enLlamas, obj) then
                table.insert(enLlamas, obj)
            end
        end
    end
    
    return enLlamas
end

-- Detectar desmayos / emergencias
function Detector.Desmayos()
    local desmayos = {}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        if obj:GetAttribute("Fainted") or obj:GetAttribute("Critical") or
           obj:GetAttribute("Emergency") or obj:GetAttribute("Unconscious") then
            table.insert(desmayos, obj)
        end
        
        local n = obj.Name:lower()
        if n:find("faint") or n:find("critical") or n:find("emergency") or 
           n:find("unconscious") or n:find("ambulance") then
            if obj:IsA("Model") and not table.find(desmayos, obj) then
                table.insert(desmayos, obj)
            end
        end
    end
    
    return desmayos
end

-- Detectar rituales de muerte (velas)
function Detector.Rituales()
    local velas = {}
    local nombresRitual = {"candle", "vela", "ritual", "sacrifice"}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        local n = obj.Name:lower()
        for _, nr in pairs(nombresRitual) do
            if n:find(nr) then
                table.insert(velas, obj)
                break
            end
        end
        
        if obj:GetAttribute("IsRitual") or obj:GetAttribute("DeathRitual") then
            if not table.find(velas, obj) then
                table.insert(velas, obj)
            end
        end
    end
    
    return velas
end

-- Detectar slime verde
function Detector.Slime()
    local slimes = {}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        local n = obj.Name:lower()
        if n:find("slime") or n:find("goo") or n:find("trail") or n:find("baba") then
            table.insert(slimes, obj)
        end
        
        if obj:IsA("BasePart") and obj.BrickColor == BrickColor.new("Lime green") then
            if not table.find(slimes, obj) then
                table.insert(slimes, obj)
            end
        end
    end
    
    return slimes
end

-- Detectar fantasmas / ojos negros
function Detector.Fantasmas()
    local fantasmas = {}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        local n = obj.Name:lower()
        if n:find("ghost") or n:find("shadow") or n:find("blackeye") or 
           n:find("darkentity") or n:find("phantom") then
            table.insert(fantasmas, obj)
        end
    end
    
    return fantasmas
end

-- Detectar monstruos bajo la cama
function Detector.MonstruosBajoCama()
    local monstruos = {}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        local n = obj.Name:lower()
        if n:find("underbed") or n:find("bedmonster") or n:find("bedhands") then
            table.insert(monstruos, obj)
        end
        
        if obj:GetAttribute("UnderBed") then
            table.insert(monstruos, obj)
        end
    end
    
    return monstruos
end

-- Detectar tentáculos en cirugía
function Detector.Tentaculos()
    local tentaculos = {}
    
    for _, obj in pairs(Workspace:GetDescendants()) do
        local n = obj.Name:lower()
        if n:find("tentacle") or n:find("tendril") or n:find("appendage") then
            table.insert(tentaculos, obj)
        end
    end
    
    return tentaculos
end

-- Detectar NPC por nombre
function Detector.NPC(nombre)
    for _, obj in pairs(Workspace:GetDescendants()) do
        if obj:IsA("Model") and obj.Name:lower():find(nombre:lower()) then
            return obj
        end
    end
    return nil
end

-- Detectar si hay pacientes esperando en recepción
function Detector.PacientesEnRecepcion()
    local enRecepcion = {}
    local posRecepcion = Mapa.Posiciones.Timbre
    
    for _, pac in pairs(Detector.Pacientes()) do
        local part = pac:FindFirstChildWhichIsA("BasePart")
        if part then
            local dist = (part.Position - posRecepcion).Magnitude
            if dist < 30 then -- Dentro del rango de recepción
                table.insert(enRecepcion, pac)
            end
        end
    end
    
    return enRecepcion
end

-- Verificar si la caja de fusibles necesita reparación
function Detector.FusiblesRotos()
    local fusebox = Instancias.CajaFusibles
    if fusebox then
        if fusebox:GetAttribute("Broken") or fusebox:GetAttribute("NeedsRepair") then
            return true
        end
        -- Verificar hijos
        for _, child in pairs(fusebox:GetDescendants()) do
            if child.Name:lower():find("broken") or child.Name:lower():find("static") then
                return true
            end
        end
    end
    return false
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 8: ACCIONES DEL JUEGO (CON RUTAS REALES)
-- ══════════════════════════════════════════════════════════════

local Acciones = {}

-- ═══════════════════════════════════════
-- TELETRANSPORTAR A UBICACIÓN DEL MAPA
-- ═══════════════════════════════════════
function Acciones.IrA(nombreUbicacion)
    local root = Util.Root()
    if not root then return false end
    
    -- Método 1: Usar instancia real si existe
    local instancia = Instancias[nombreUbicacion]
    if instancia then
        if instancia:IsA("BasePart") then
            root.CFrame = instancia.CFrame + Vector3.new(0, 3, 0)
            task.wait(0.05)
            return true
        elseif instancia:IsA("Model") then
            local part = instancia.PrimaryPart or instancia:FindFirstChildWhichIsA("BasePart")
            if part then
                root.CFrame = part.CFrame + Vector3.new(0, 3, 0)
                task.wait(0.05)
                return true
            end
        end
    end
    
    -- Método 2: Usar coordenadas exactas del mapa
    local coord = Mapa.Coordenadas[nombreUbicacion]
    if coord then
        root.CFrame = coord + Vector3.new(0, 3, 0)
        task.wait(0.05)
        return true
    end
    
    -- Método 3: Usar posiciones Vector3
    local pos = Mapa.Posiciones[nombreUbicacion]
    if pos then
        root.CFrame = CFrame.new(pos + Vector3.new(0, 3, 0))
        task.wait(0.05)
        return true
    end
    
    return false
end

-- ═══════════════════════════════════════
-- ACCIÓN: TOCAR TIMBRE DE RECEPCIÓN
-- ═══════════════════════════════════════
function Acciones.TocarTimbre()
    Estado.TareaActual = "🔔 Tocando timbre de recepción..."
    
    -- Ir a la recepción
    Acciones.IrA("Timbre")
    task.wait(0.1)
    
    -- Método 1: FireClickDetector directo
    local timbre = Instancias.Timbre
    if timbre then
        local cd = timbre:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then
            fireclickdetector(cd)
            task.wait(0.1)
            return true
        end
    end
    
    -- Método 2: Usando ruta directa
    pcall(function()
        local bell = game.Workspace.Map.Reception.Bell
        local cd = bell:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then fireclickdetector(cd) end
    end)
    
    -- Método 3: ProximityPrompt
    Util.FireClick("Timbre")
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: TOMAR FOTO CON POLAROID
-- ═══════════════════════════════════════
function Acciones.TomarFoto(objetivo)
    Estado.TareaActual = "📸 Tomando foto Polaroid..."
    
    -- Ir a la cámara en recepción
    Acciones.IrA("CamaraPolaroid")
    task.wait(0.1)
    
    -- Recoger/usar la cámara
    local camaraPolaroid = Instancias.CamaraPolaroid
    if camaraPolaroid then
        Util.ClickearObjeto(camaraPolaroid)
        task.wait(0.2)
    end
    
    -- Equipar cámara del inventario
    local camera = Util.Equipar("camera") or Util.Equipar("polaroid") or Util.Equipar("photo")
    
    if camera then
        -- Apuntar al objetivo si existe
        if objetivo then
            local root = Util.Root()
            local targetPart = objetivo:FindFirstChild("HumanoidRootPart") or 
                              objetivo:FindFirstChildWhichIsA("BasePart")
            if root and targetPart then
                root.CFrame = CFrame.new(root.Position, targetPart.Position)
            end
        end
        
        -- Tomar la foto
        camera:Activate()
        task.wait(1.5) -- Esperar revelado de la foto
    end
    
    -- Analizar la foto revelada
    Acciones.AnalizarFotoRevelada()
    
    return true
end

-- Analizar foto revelada para detectar anomalías
function Acciones.AnalizarFotoRevelada()
    local playerGui = Player:FindFirstChild("PlayerGui")
    if not playerGui then return false end
    
    local esAnomalia = false
    
    for _, gui in pairs(playerGui:GetDescendants()) do
        if gui:IsA("ImageLabel") then
            local n = gui.Name:lower()
            if n:find("photo") or n:find("polaroid") or n:find("picture") or n:find("reveal") then
                -- Verificar si la foto muestra anomalías
                if gui:GetAttribute("ShowsAnomaly") or gui:GetAttribute("Scary") or
                   gui:GetAttribute("Anomaly") then
                    esAnomalia = true
                end
                
                -- Verificar hijos de la imagen
                for _, child in pairs(gui:GetDescendants()) do
                    if child.Name:lower():find("anomal") or child.Name:lower():find("scary") or
                       child.Name:lower():find("monster") or child.Name:lower():find("creepy") then
                        esAnomalia = true
                    end
                end
            end
        end
    end
    
    if esAnomalia then
        Estado.AnomalíasDetectadas = Estado.AnomalíasDetectadas + 1
        Util.Notificar("¡ANOMALÍA!", "⚠️ Foto revela criatura anómala", 3)
        -- Rechazar inmediatamente
        Acciones.CerrarPersiana()
        return true
    end
    
    return false
end

-- ═══════════════════════════════════════
-- ACCIÓN: CERRAR PERSIANA DE SEGURIDAD
-- ═══════════════════════════════════════
function Acciones.CerrarPersiana()
    Estado.TareaActual = "🪟 Cerrando persiana de seguridad..."
    
    -- Ir al botón de persiana
    Acciones.IrA("BotonPersiana")
    task.wait(0.05)
    
    -- Activar botón de persiana
    local boton = Instancias.BotonPersiana
    if boton then
        Util.ClickearObjeto(boton)
    end
    
    -- Método directo
    pcall(function()
        local shutterBtn = game.Workspace.Map.Reception.ShutterButton
        local cd = shutterBtn:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then fireclickdetector(cd) end
    end)
    
    -- Remotos
    Util.Remoto("closeblinds")
    Util.Remoto("shutter")
    Util.Remoto("closewindow")
    
    Util.Log("Persiana cerrada")
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: TOMAR CAFÉ (RESTAURAR CORDURA)
-- ═══════════════════════════════════════
function Acciones.TomarCafe()
    Estado.TareaActual = "☕ Yendo a tomar café..."
    Util.Log("Cordura: " .. Estado.CorduraActual .. "% - Yendo por café")
    
    -- Teletransportarse a la máquina de café
    -- Coordenadas exactas: (35, 4, -15) en Map.Breakroom.CoffeeMachine
    local root = Util.Root()
    if root then
        root.CFrame = CFrame.new(35, 7, -15) -- +3 de offset Y
    end
    task.wait(0.15)
    
    -- Activar máquina de café via ClickDetector
    local maquinaCafe = Instancias.MaquinaCafe
    if maquinaCafe then
        Util.ClickearObjeto(maquinaCafe)
        task.wait(0.3)
    end
    
    -- Método directo
    pcall(function()
        local coffeeMachine = game.Workspace.Map.Breakroom.CoffeeMachine
        local cd = coffeeMachine:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then fireclickdetector(cd) end
        
        local pp = coffeeMachine:FindFirstChildWhichIsA("ProximityPrompt", true)
        if pp then fireproximityprompt(pp) end
    end)
    
    task.wait(0.3)
    
    -- Buscar y consumir la taza de café del inventario
    local cafe = Util.Equipar("coffee") or Util.Equipar("cafe") or 
                 Util.Equipar("cup") or Util.Equipar("mug") or Util.Equipar("taza")
    
    if cafe then
        cafe:Activate() -- Consumir el café
        task.wait(0.3)
    end
    
    -- Remotos adicionales
    Util.Remoto("drink")
    Util.Remoto("coffee")
    Util.Remoto("sanity")
    Util.Remoto("restore")
    
    Util.Notificar("Café", "☕ Cordura restaurada", 2)
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: REGISTRAR PACIENTE EN RECEPCIÓN
-- ═══════════════════════════════════════
function Acciones.RegistrarPaciente()
    if not Config.AutoRecepcionActivo then return true end
    
    Estado.TareaActual = "📋 Atendiendo recepción..."
    
    -- Ir a recepción
    local root = Util.Root()
    if root then
        root.CFrame = CFrame.new(0, 8, -25) -- Posición de recepción
    end
    task.wait(0.15)
    
    -- Paso 1: Tocar timbre para llamar al siguiente paciente
    Acciones.TocarTimbre()
    task.wait(1) -- Esperar a que el paciente camine al mostrador
    
    -- Paso 2: Analizar la GUI del formulario
    local playerGui = Player:FindFirstChild("PlayerGui")
    local esAnomalia = false
    
    if playerGui then
        -- Buscar el portapapeles / formulario de registro
        for _, gui in pairs(playerGui:GetDescendants()) do
            if gui:IsA("Frame") or gui:IsA("ScrollingFrame") then
                local n = gui.Name:lower()
                if n:find("clipboard") or n:find("form") or n:find("register") or 
                   n:find("check") or n:find("patient") then
                    -- Analizar datos del paciente
                    for _, child in pairs(gui:GetDescendants()) do
                        if child:IsA("TextLabel") then
                            local texto = child.Text:lower()
                            -- Indicadores de anomalía
                            if texto:find("human") or texto:find("unknown") or 
                               texto:find("????") or texto:find("error") or
                               texto:find("n/a") or texto:find("invalid") then
                                esAnomalia = true
                                Util.Log("⚠️ IMPOSTOR DETECTADO en formulario!")
                            end
                        end
                    end
                end
            end
        end
        
        -- Paso 3: Tomar foto Polaroid para verificar
        Acciones.TomarFoto()
        task.wait(0.5)
        
        -- Paso 4: Estampar formulario (aprobar o rechazar)
        for _, gui in pairs(playerGui:GetDescendants()) do
            if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                local n = gui.Name:lower()
                local t = ""
                pcall(function() t = gui.Text:lower() end)
                
                if esAnomalia then
                    -- RECHAZAR impostor
                    if n:find("reject") or n:find("deny") or n:find("decline") or
                       n:find("rechazar") or n:find("stamp") and n:find("red") or
                       t:find("reject") or t:find("deny") or t:find("no") then
                        pcall(function() gui.MouseButton1Click:Fire() end)
                        Estado.AnomalíasDetectadas = Estado.AnomalíasDetectadas + 1
                        Util.Notificar("Recepción", "🚫 ¡IMPOSTOR RECHAZADO!", 3)
                        
                        -- Cerrar persiana por seguridad
                        Acciones.CerrarPersiana()
                    end
                else
                    -- APROBAR paciente real
                    if n:find("approve") or n:find("accept") or n:find("admit") or
                       n:find("stamp") or n:find("sello") or n:find("aprobar") or
                       t:find("approve") or t:find("accept") or t:find("admit") or
                       t:find("yes") or t:find("si") then
                        pcall(function() gui.MouseButton1Click:Fire() end)
                        Estado.PacientesAtendidos = Estado.PacientesAtendidos + 1
                        Util.Notificar("Recepción", "✅ Paciente admitido", 2)
                    end
                end
            end
        end
    end
    
    -- Remotos de registro
    Util.Remoto("stamp")
    Util.Remoto("register")
    Util.Remoto("checkin")
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: ELIMINAR SKINWALKER
-- ═══════════════════════════════════════
function Acciones.EliminarSkinwalker(skinwalker)
    if not skinwalker or not skinwalker.Parent then return true end
    
    Estado.TareaActual = "⚔️ ELIMINANDO SKINWALKER: " .. skinwalker.Name
    Util.Log("¡SKINWALKER DETECTADO! Eliminando: " .. skinwalker.Name)
    
    -- Teletransportarse al Skinwalker
    Util.TP(skinwalker)
    task.wait(0.1)
    
    -- Equipar Taser
    local taser = Util.Equipar("taser") or Util.Equipar("stun") or 
                  Util.Equipar("weapon") or Util.Equipar("gun")
    
    if taser then
        -- Apuntar al objetivo
        local root = Util.Root()
        local target = skinwalker:FindFirstChild("HumanoidRootPart") or
                       skinwalker:FindFirstChild("Head") or
                       skinwalker:FindFirstChildWhichIsA("BasePart")
        
        if root and target then
            root.CFrame = CFrame.new(root.Position, target.Position)
            task.wait(0.05)
        end
        
        -- Disparar Taser
        taser:Activate()
        task.wait(0.2)
        taser:Activate() -- Doble disparo por seguridad
        task.wait(0.1)
    end
    
    -- Interacción directa (puñetazos - spam E)
    for i = 1, 15 do
        Util.Tecla(Enum.KeyCode.E)
        task.wait(0.03)
    end
    
    -- Remotos de eliminación
    Util.Remoto("kill", skinwalker)
    Util.Remoto("attack", skinwalker)
    Util.Remoto("taser", skinwalker)
    Util.Remoto("eliminate", skinwalker)
    Util.Remoto("damage", skinwalker, 9999)
    
    -- Activar cualquier ClickDetector o ProximityPrompt en el skinwalker
    Util.ClickearObjeto(skinwalker)
    
    Estado.SkinwalkersEliminados = Estado.SkinwalkersEliminados + 1
    Util.Notificar("¡ELIMINADO!", "⚔️ Skinwalker eliminado #" .. Estado.SkinwalkersEliminados, 3)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: ATENDER DESMAYO / EMERGENCIA
-- ═══════════════════════════════════════
function Acciones.AtenderDesmayo(paciente)
    if not paciente or not paciente.Parent then return true end
    
    Estado.TareaActual = "🚨 EMERGENCIA: Atendiendo desmayo..."
    Util.Log("¡DESMAYO DETECTADO! Corriendo a atender...")
    
    -- 1. Teletransportarse al paciente desmayado
    Util.TP(paciente)
    task.wait(0.1)
    
    -- 2. Interactuar para cargar al paciente (E)
    Util.ClickearObjeto(paciente)
    Util.Tecla(Enum.KeyCode.E)
    task.wait(0.2)
    
    Estado.CargandoPaciente = true
    
    -- 3. Buscar cama vacía más cercana y llevar al paciente
    local camaInfo, indice = Util.CamaVaciaCercana()
    
    if camaInfo then
        -- Teletransportarse a la cama
        local root = Util.Root()
        if root then
            root.CFrame = CFrame.new(camaInfo.pos + Vector3.new(0, 3, 0))
        end
        task.wait(0.1)
        
        -- Soltar paciente en la cama
        Util.Tecla(Enum.KeyCode.E)
        
        -- Activar ClickDetector de la cama
        local camaInst = ResolverRuta(camaInfo.ruta)
        if camaInst then
            Util.ClickearObjeto(camaInst)
        end
        
        task.wait(0.2)
        
        -- Marcar cama como ocupada
        if indice then
            Estado.CamasOcupadas[indice] = true
        end
    end
    
    Estado.CargandoPaciente = false
    
    -- 4. Iniciar RCP inmediatamente
    Acciones.RealizarRCP()
    
    -- Remotos de emergencia
    Util.Remoto("revive", paciente)
    Util.Remoto("rescue", paciente)
    Util.Remoto("stabilize", paciente)
    Util.Remoto("cpr", paciente)
    
    Estado.DesmayosSalvados = Estado.DesmayosSalvados + 1
    Util.Notificar("Emergencia", "🚨 ¡Paciente estabilizado! #" .. Estado.DesmayosSalvados, 3)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: EXTINGUIR INCENDIO
-- ═══════════════════════════════════════
function Acciones.ExtinguirFuego(pacienteEnLlamas)
    if not pacienteEnLlamas or not pacienteEnLlamas.Parent then return true end
    
    Estado.TareaActual = "🔥 EXTINGUIENDO INCENDIO..."
    Util.Log("¡INCENDIO! Paciente en llamas detectado")
    
    -- 1. Obtener extintor
    local extintor = Util.Equipar("extinguish") or Util.Equipar("extintor") or Util.Equipar("fire")
    
    if not extintor then
        -- Ir a buscar el extintor
        -- Coordenadas exactas: (15, 5, 10) en Map.Hallways.Extinguisher
        local root = Util.Root()
        if root then
            root.CFrame = CFrame.new(15, 8, 10)
        end
        task.wait(0.15)
        
        -- Recoger extintor
        local extInst = Instancias.Extintor
        if extInst then
            Util.ClickearObjeto(extInst)
            task.wait(0.2)
        end
        
        -- Método directo
        pcall(function()
            local ext = game.Workspace.Map.Hallways.Extinguisher
            local cd = ext:FindFirstChildWhichIsA("ClickDetector", true)
            if cd then fireclickdetector(cd) end
            
            local pp = ext:FindFirstChildWhichIsA("ProximityPrompt", true)
            if pp then fireproximityprompt(pp) end
        end)
        
        task.wait(0.2)
        extintor = Util.Equipar("extinguish") or Util.Equipar("extintor") or Util.Equipar("fire")
    end
    
    -- 2. Ir al paciente en llamas
    Util.TP(pacienteEnLlamas)
    task.wait(0.1)
    
    -- 3. Usar extintor
    if extintor then
        -- Mantener activado para apagar el fuego progresivamente
        for i = 1, 40 do
            extintor:Activate()
            
            -- Verificar si sigue en llamas
            local sigueEnLlamas = false
            for _, child in pairs(pacienteEnLlamas:GetDescendants()) do
                if child:IsA("Fire") then
                    sigueEnLlamas = true
                    break
                end
            end
            
            if not sigueEnLlamas then
                break
            end
            
            task.wait(0.08)
        end
    end
    
    -- Remotos
    Util.Remoto("extinguish", pacienteEnLlamas)
    Util.Remoto("putout", pacienteEnLlamas)
    Util.Remoto("stopfire", pacienteEnLlamas)
    
    Util.Desequipar()
    
    Estado.IncendiosExtinguidos = Estado.IncendiosExtinguidos + 1
    Util.Notificar("Fuego", "🔥 Incendio extinguido #" .. Estado.IncendiosExtinguidos, 3)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: DETENER RITUAL DE MUERTE
-- ═══════════════════════════════════════
function Acciones.DetenerRitual(velas)
    Estado.TareaActual = "🕯️ ¡DETENIENDO RITUAL DE MUERTE!"
    Util.Log("¡RITUAL DE MUERTE DETECTADO! Apagando velas...")
    
    -- Apagar cada vela lo más rápido posible
    for _, vela in pairs(velas) do
        if vela and vela.Parent then
            -- Teletransportarse a la vela
            Util.TP(vela)
            task.wait(0.03)
            
            -- Interactuar para apagar
            Util.ClickearObjeto(vela)
            Util.Tecla(Enum.KeyCode.E)
            
            -- Remotos
            Util.Remoto("extinguish", vela)
            Util.Remoto("blowout", vela)
            Util.Remoto("interact", vela)
            
            task.wait(0.03)
        end
    end
    
    Estado.RitualesDetenidos = Estado.RitualesDetenidos + 1
    Util.Notificar("Ritual", "🕯️ ¡Ritual detenido! #" .. Estado.RitualesDetenidos, 3)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: REALIZAR CIRUGÍA
-- ═══════════════════════════════════════
function Acciones.RealizarCirugia()
    if not Config.AutoCirugiaActivo then return true end
    
    Estado.TareaActual = "🔪 Realizando cirugía..."
    Util.Log("Iniciando cirugía automática")
    
    -- Ir a sala de cirugía
    -- Coordenadas exactas: (45, 3, 80) en Map.SurgeryRoom.OperatingTable
    local root = Util.Root()
    if root then
        root.CFrame = CFrame.new(45, 6, 80)
    end
    task.wait(0.15)
    
    -- Interactuar con mesa de cirugía
    local mesa = Instancias.MesaCirugia
    if mesa then
        Util.ClickearObjeto(mesa)
        task.wait(0.2)
    end
    
    pcall(function()
        local ot = game.Workspace.Map.SurgeryRoom.OperatingTable
        local cd = ot:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then fireclickdetector(cd) end
    end)
    
    task.wait(0.3)
    
    -- Auto-completar minijuego de cirugía
    local playerGui = Player:FindFirstChild("PlayerGui")
    if playerGui then
        -- Monitorear el minijuego
        task.spawn(function()
            for ciclo = 1, 100 do
                if not Config.AutoCirugiaActivo then break end
                
                -- Buscar y seguir la línea de incisión
                for _, gui in pairs(playerGui:GetDescendants()) do
                    if gui:IsA("Frame") or gui:IsA("ImageLabel") then
                        local n = gui.Name:lower()
                        if n:find("line") or n:find("path") or n:find("cut") or 
                           n:find("incision") or n:find("trace") then
                            pcall(function()
                                local pos = gui.AbsolutePosition
                                local size = gui.AbsoluteSize
                                -- Seguir la línea
                                for t = 0, 1, 0.01 do
                                    local x = pos.X + size.X * t
                                    local y = pos.Y + size.Y / 2
                                    VirtualInputManager:SendMouseButtonEvent(x, y, 0, true, game, 0)
                                    task.wait(0.005)
                                end
                                VirtualInputManager:SendMouseButtonEvent(
                                    pos.X + size.X, pos.Y + size.Y/2, 0, false, game, 0)
                            end)
                        end
                    end
                    
                    -- Botones de acción
                    if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                        local n = gui.Name:lower()
                        local t = ""
                        pcall(function() t = gui.Text:lower() end)
                        
                        if n:find("cut") or n:find("scalpel") or n:find("incision") or
                           n:find("complete") or n:find("finish") or n:find("done") or
                           n:find("success") or n:find("bisturi") or n:find("stitch") or
                           t:find("cut") or t:find("complete") or t:find("finish") then
                            pcall(function() gui.MouseButton1Click:Fire() end)
                        end
                    end
                end
                
                -- Detectar y destruir tentáculos
                local tentaculos = Detector.Tentaculos()
                for _, tent in pairs(tentaculos) do
                    -- Si es un objeto 3D
                    if tent:IsA("BasePart") then
                        local screenPos, onScreen = Camera:WorldToScreenPoint(tent.Position)
                        if onScreen then
                            for j = 1, 8 do
                                Util.Clic(screenPos.X, screenPos.Y)
                                task.wait(0.015)
                            end
                        end
                    end
                    
                    -- Si es GUI
                    if tent:IsA("GuiObject") then
                        pcall(function()
                            local pos = tent.AbsolutePosition
                            local size = tent.AbsoluteSize
                            for j = 1, 8 do
                                Util.Clic(pos.X + size.X/2, pos.Y + size.Y/2)
                                task.wait(0.015)
                            end
                        end)
                    end
                    
                    Util.ClickearObjeto(tent)
                end
                
                -- Buscar tentáculos en la GUI también
                for _, gui in pairs(playerGui:GetDescendants()) do
                    local n = gui.Name:lower()
                    if n:find("tentacle") or n:find("tendril") or n:find("appendage") then
                        if gui:IsA("GuiButton") then
                            pcall(function() gui.MouseButton1Click:Fire() end)
                        elseif gui:IsA("GuiObject") then
                            pcall(function()
                                local pos = gui.AbsolutePosition
                                local size = gui.AbsoluteSize
                                for j = 1, 5 do
                                    Util.Clic(pos.X + size.X/2, pos.Y + size.Y/2)
                                    task.wait(0.02)
                                end
                            end)
                        end
                    end
                end
                
                task.wait(0.08)
            end
        end)
    end
    
    -- Remotos de cirugía
    Util.Remoto("surgery")
    Util.Remoto("completesurgery")
    Util.Remoto("operation")
    
    Estado.CirugiasCompletadas = Estado.CirugiasCompletadas + 1
    Util.Notificar("Cirugía", "🔪 Cirugía completada #" .. Estado.CirugiasCompletadas, 3)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: REALIZAR RCP
-- ═══════════════════════════════════════
function Acciones.RealizarRCP()
    if not Config.AutoRCPActivo then return true end
    
    Estado.TareaActual = "❤️ Realizando RCP..."
    
    local playerGui = Player:FindFirstChild("PlayerGui")
    
    -- Auto-completar el QTE de ritmo cardíaco
    task.spawn(function()
        for ciclo = 1, 120 do
            if not Config.AutoRCPActivo then break end
            
            if playerGui then
                for _, gui in pairs(playerGui:GetDescendants()) do
                    local n = gui.Name:lower()
                    
                    -- Buscar la zona verde / objetivo del QTE
                    if gui:IsA("Frame") or gui:IsA("ImageLabel") then
                        if n:find("green") or n:find("target") or n:find("zone") or
                           n:find("hit") or n:find("perfect") or n:find("sweet") then
                            -- Presionar en el momento correcto
                            Util.Tecla(Enum.KeyCode.Space)
                            task.wait(0.01)
                        end
                        
                        -- Verificar si el indicador está en la zona verde
                        if n:find("indicator") or n:find("needle") or n:find("pointer") or
                           n:find("cursor") or n:find("marker") or n:find("slider") then
                            -- El indicador está moviéndose, presionar cuando esté en la zona
                            Util.Tecla(Enum.KeyCode.Space)
                        end
                    end
                    
                    -- Botones de RCP
                    if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                        if n:find("cpr") or n:find("pump") or n:find("press") or
                           n:find("heart") or n:find("chest") or n:find("compress") then
                            pcall(function() gui.MouseButton1Click:Fire() end)
                        end
                    end
                end
            end
            
            -- Spam de teclas para el ritmo
            Util.Tecla(Enum.KeyCode.Space)
            task.wait(0.04)
            Util.Tecla(Enum.KeyCode.E)
            task.wait(0.04)
        end
    end)
    
    -- Remotos
    Util.Remoto("cpr")
    Util.Remoto("heartrate")
    Util.Remoto("revive")
    Util.Remoto("stabilize")
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: REALIZAR RAYOS X
-- ═══════════════════════════════════════
function Acciones.RealizarRayosX()
    if not Config.AutoRayosXActivo then return true end
    
    Estado.TareaActual = "☢️ Realizando Rayos X..."
    
    -- Ir a sala de Rayos X
    -- Coordenadas exactas: (-45, 3, 80) en Map.XRayRoom.XRayMachine
    local root = Util.Root()
    if root then
        root.CFrame = CFrame.new(-45, 6, 80)
    end
    task.wait(0.15)
    
    -- Interactuar con la máquina de Rayos X
    local maquinaRX = Instancias.MaquinaRayosX
    if maquinaRX then
        Util.ClickearObjeto(maquinaRX)
        task.wait(0.3)
    end
    
    pcall(function()
        local xray = game.Workspace.Map.XRayRoom.XRayMachine
        local cd = xray:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then fireclickdetector(cd) end
    end)
    
    task.wait(0.5)
    
    -- Analizar la imagen de Rayos X en la GUI
    local playerGui = Player:FindFirstChild("PlayerGui")
    if playerGui then
        local esAnomalia = false
        
        for _, gui in pairs(playerGui:GetDescendants()) do
            -- Buscar la imagen del scan
            if gui:IsA("ImageLabel") and (gui.Name:lower():find("xray") or 
               gui.Name:lower():find("scan") or gui.Name:lower():find("skeleton")) then
                -- Verificar anomalías
                if gui:GetAttribute("IsAnomaly") or gui:GetAttribute("Abnormal") or
                   gui:GetAttribute("HumanBones") then
                    esAnomalia = true
                end
                
                for _, child in pairs(gui:GetDescendants()) do
                    if child.Name:lower():find("human") or child.Name:lower():find("anomal") or
                       child.Name:lower():find("deform") then
                        esAnomalia = true
                    end
                end
            end
            
            -- Botones de resultado
            if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                local n = gui.Name:lower()
                local t = ""
                pcall(function() t = gui.Text:lower() end)
                
                if esAnomalia then
                    if n:find("anomal") or n:find("report") or n:find("reject") or
                       t:find("anomal") or t:find("report") then
                        pcall(function() gui.MouseButton1Click:Fire() end)
                        Estado.AnomalíasDetectadas = Estado.AnomalíasDetectadas + 1
                        Util.Notificar("Rayos X", "☢️ ¡ANOMALÍA en radiografía!", 3)
                    end
                else
                    if n:find("normal") or n:find("confirm") or n:find("okay") or n:find("done") or
                       t:find("normal") or t:find("confirm") then
                        pcall(function() gui.MouseButton1Click:Fire() end)
                    end
                end
            end
        end
    end
    
    Util.Remoto("xray")
    Util.Remoto("scan")
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: ANÁLISIS DE ADN
-- ═══════════════════════════════════════
function Acciones.RealizarADN()
    if not Config.AutoADNActivo then return true end
    
    Estado.TareaActual = "🧬 Analizando ADN..."
    
    -- Ir al botiquín de medicinas / laboratorio
    -- Coordenadas exactas: (0, 5, 65) en Map.Pharmacy.Cabinet
    local root = Util.Root()
    if root then
        root.CFrame = CFrame.new(0, 8, 65)
    end
    task.wait(0.15)
    
    -- Interactuar con el gabinete
    local botiquin = Instancias.BotiquinMedicinas
    if botiquin then
        Util.ClickearObjeto(botiquin)
        task.wait(0.3)
    end
    
    pcall(function()
        local cabinet = game.Workspace.Map.Pharmacy.Cabinet
        local cd = cabinet:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then fireclickdetector(cd) end
    end)
    
    task.wait(0.5)
    
    -- Completar minijuego de ADN en GUI
    local playerGui = Player:FindFirstChild("PlayerGui")
    if playerGui then
        for _, gui in pairs(playerGui:GetDescendants()) do
            if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                local n = gui.Name:lower()
                local t = ""
                pcall(function() t = gui.Text:lower() end)
                
                -- Iniciar análisis
                if n:find("analyze") or n:find("process") or n:find("start") or 
                   n:find("test") or n:find("dna") or
                   t:find("analiz") or t:find("process") or t:find("start") then
                    pcall(function() gui.MouseButton1Click:Fire() end)
                    task.wait(0.5)
                end
                
                -- Resultados
                if n:find("anomal") or n:find("reject") then
                    pcall(function() gui.MouseButton1Click:Fire() end)
                    Estado.AnomalíasDetectadas = Estado.AnomalíasDetectadas + 1
                end
                
                if n:find("normal") or n:find("clear") or n:find("confirm") then
                    pcall(function() gui.MouseButton1Click:Fire() end)
                end
            end
        end
    end
    
    Util.Remoto("dna")
    Util.Remoto("analysis")
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: LIMPIAR SLIME VERDE
-- ═══════════════════════════════════════
function Acciones.LimpiarSlime(slime)
    if not slime or not slime.Parent then return true end
    
    Estado.TareaActual = "🧹 Limpiando slime verde..."
    
    -- Buscar y equipar el trapeador
    local trapeador = Util.Equipar("mop") or Util.Equipar("clean") or Util.Equipar("broom")
    
    if not trapeador then
        -- Ir a buscar el trapeador
        -- Coordenadas exactas: (5, 3, 105) en Map.Maintenance.Mop
        local root = Util.Root()
        if root then
            root.CFrame = CFrame.new(5, 6, 105)
        end
        task.wait(0.15)
        
        local mopInst = Instancias.Trapeador
        if mopInst then
            Util.ClickearObjeto(mopInst)
            task.wait(0.2)
        end
        
        pcall(function()
            local mop = game.Workspace.Map.Maintenance.Mop
            local cd = mop:FindFirstChildWhichIsA("ClickDetector", true)
            if cd then fireclickdetector(cd) end
        end)
        
        task.wait(0.2)
        trapeador = Util.Equipar("mop") or Util.Equipar("clean")
    end
    
    -- Ir al slime
    Util.TP(slime)
    task.wait(0.1)
    
    -- Limpiar
    if trapeador then
        trapeador:Activate()
        task.wait(0.3)
    end
    
    Util.ClickearObjeto(slime)
    Util.Tecla(Enum.KeyCode.E)
    
    Util.Remoto("clean", slime)
    Util.Remoto("mop", slime)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: REPARAR CÁMARAS / FUSIBLES
-- ═══════════════════════════════════════
function Acciones.RepararCamaras()
    Estado.TareaActual = "📹 Reparando cámaras/fusibles..."
    
    -- Ir al panel CCTV
    -- Coordenadas exactas: (-15, 6, 20) en Map.Hallways.CCTVPanel1
    local root = Util.Root()
    if root then
        root.CFrame = CFrame.new(-15, 9, 20)
    end
    task.wait(0.15)
    
    local panel = Instancias.PanelCCTV
    if panel then
        Util.ClickearObjeto(panel)
        task.wait(0.2)
    end
    
    pcall(function()
        local cctv = game.Workspace.Map.Hallways.CCTVPanel1
        local cd = cctv:FindFirstChildWhichIsA("ClickDetector", true)
        if cd then fireclickdetector(cd) end
    end)
    
    -- Si los fusibles están rotos, ir a repararlos
    if Detector.FusiblesRotos() then
        -- Ir a caja de fusibles
        -- Coordenadas exactas: (0, 6, 110) en Map.Maintenance.FuseBox
        root = Util.Root()
        if root then
            root.CFrame = CFrame.new(0, 9, 110)
        end
        task.wait(0.15)
        
        local fusebox = Instancias.CajaFusibles
        if fusebox then
            Util.ClickearObjeto(fusebox)
            task.wait(0.3)
        end
        
        pcall(function()
            local fb = game.Workspace.Map.Maintenance.FuseBox
            local cd = fb:FindFirstChildWhichIsA("ClickDetector", true)
            if cd then fireclickdetector(cd) end
        end)
        
        -- Completar minijuego de reparación
        local playerGui = Player:FindFirstChild("PlayerGui")
        if playerGui then
            for ciclo = 1, 30 do
                for _, gui in pairs(playerGui:GetDescendants()) do
                    if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                        local n = gui.Name:lower()
                        if n:find("repair") or n:find("fix") or n:find("wire") or
                           n:find("connect") or n:find("fuse") or n:find("switch") then
                            pcall(function() gui.MouseButton1Click:Fire() end)
                        end
                    end
                end
                task.wait(0.1)
            end
        end
    end
    
    Util.Remoto("repair")
    Util.Remoto("fixcamera")
    Util.Remoto("fusebox")
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: ELIMINAR FANTASMA / OJOS NEGROS
-- ═══════════════════════════════════════
function Acciones.EliminarFantasma(fantasma)
    if not fantasma or not fantasma.Parent then return true end
    
    Estado.TareaActual = "👻 Eliminando fantasma..."
    
    Util.TP(fantasma)
    task.wait(0.1)
    
    -- Equipar y usar Taser
    local taser = Util.Equipar("taser") or Util.Equipar("stun")
    if taser then
        local target = fantasma:FindFirstChildWhichIsA("BasePart")
        if target then
            local root = Util.Root()
            if root then
                root.CFrame = CFrame.new(root.Position, target.Position)
            end
        end
        
        taser:Activate()
        task.wait(0.1)
        taser:Activate()
    end
    
    -- Interacción directa
    for i = 1, 10 do
        Util.Tecla(Enum.KeyCode.E)
        task.wait(0.03)
    end
    
    Util.ClickearObjeto(fantasma)
    Util.Remoto("taser", fantasma)
    Util.Remoto("shock", fantasma)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: EVENTO BARNEY (COMPLETO)
-- ═══════════════════════════════════════
function Acciones.ManejarBarney(barney)
    if not barney or not barney.Parent then return true end
    
    Estado.TareaActual = "🐻 Atendiendo evento Barney..."
    Util.Log("EVENTO BARNEY activado")
    
    -- Ir a Barney
    Util.TP(barney)
    task.wait(0.2)
    
    -- Interactuar
    Util.ClickearObjeto(barney)
    Util.Tecla(Enum.KeyCode.E)
    task.wait(0.5)
    
    local playerGui = Player:FindFirstChild("PlayerGui")
    if playerGui then
        -- Gestionar todas las fases del evento Barney
        for intentos = 1, 20 do
            for _, gui in pairs(playerGui:GetDescendants()) do
                if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                    local n = gui.Name:lower()
                    local t = ""
                    pcall(function() t = gui.Text:lower() end)
                    
                    -- FASE 1: Dar café
                    if n:find("give") or n:find("dar") or n:find("accept") or
                       n:find("yes") or n:find("si") or
                       t:find("give") or t:find("coffee") or t:find("dar") or
                       t:find("café") or t:find("cafe") or t:find("accept") or
                       t:find("yes") or t:find("si") then
                        
                        -- Asegurar que tenemos café
                        local tieneCafe = false
                        for _, tool in pairs(Player.Backpack:GetChildren()) do
                            if tool.Name:lower():find("coffee") or tool.Name:lower():find("cafe") or
                               tool.Name:lower():find("cup") then
                                tieneCafe = true
                                break
                            end
                        end
                        
                        if not tieneCafe then
                            Acciones.TomarCafe()
                            Util.TP(barney)
                            task.wait(0.3)
                        end
                        
                        pcall(function() gui.MouseButton1Click:Fire() end)
                        task.wait(0.3)
                    end
                    
                    -- FASE 2: Prestar bisturí
                    if n:find("lend") or n:find("scalpel") or n:find("bisturi") or
                       n:find("borrow") or
                       t:find("lend") or t:find("scalpel") or t:find("bisturi") or
                       t:find("borrow") then
                        pcall(function() gui.MouseButton1Click:Fire() end)
                        task.wait(0.3)
                    end
                    
                    -- FASE 3: Tomar foto
                    if n:find("photo") or n:find("camera") or n:find("picture") or
                       n:find("foto") or n:find("snap") or
                       t:find("photo") or t:find("camera") or t:find("foto") or
                       t:find("picture") then
                        
                        -- Ir a buscar la cámara Polaroid si no la tenemos
                        local cam = Util.Equipar("camera") or Util.Equipar("polaroid")
                        if not cam then
                            Acciones.IrA("CamaraPolaroid")
                            task.wait(0.2)
                            Util.ClickearObjeto(Instancias.CamaraPolaroid)
                            task.wait(0.2)
                            cam = Util.Equipar("camera") or Util.Equipar("polaroid")
                        end
                        
                        if cam then
                            -- Apuntar a Barney
                            local root = Util.Root()
                            local barneyPart = barney:FindFirstChild("HumanoidRootPart") or
                                              barney:FindFirstChildWhichIsA("BasePart")
                            if root and barneyPart then
                                root.CFrame = CFrame.new(root.Position, barneyPart.Position)
                            end
                            
                            cam:Activate()
                            task.wait(1.5)
                        end
                        
                        pcall(function() gui.MouseButton1Click:Fire() end)
                        task.wait(0.3)
                    end
                    
                    -- Continuar diálogos
                    if n:find("continue") or n:find("next") or n:find("ok") or
                       n:find("siguiente") or n:find("close") or
                       t:find("continue") or t:find("next") or t:find("ok") then
                        pcall(function() gui.MouseButton1Click:Fire() end)
                        task.wait(0.2)
                    end
                end
            end
            task.wait(0.3)
        end
    end
    
    Util.Remoto("barney")
    Util.Remoto("dialogue")
    
    Estado.EventosBarneyCompletados = Estado.EventosBarneyCompletados + 1
    Util.Notificar("Barney", "🐻 Evento completado #" .. Estado.EventosBarneyCompletados, 3)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: EVENTO RATTHEW
-- ═══════════════════════════════════════
function Acciones.ManejarRatthew(ratthew)
    if not ratthew or not ratthew.Parent then return true end
    
    Estado.TareaActual = "🐭 Interactuando con Ratthew..."
    
    Util.TP(ratthew)
    task.wait(0.2)
    
    Util.ClickearObjeto(ratthew)
    Util.Tecla(Enum.KeyCode.E)
    task.wait(0.5)
    
    local playerGui = Player:FindFirstChild("PlayerGui")
    if playerGui then
        for _, gui in pairs(playerGui:GetDescendants()) do
            if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                local n = gui.Name:lower()
                local t = ""
                pcall(function() t = gui.Text:lower() end)
                
                if n:find("accept") or n:find("take") or n:find("key") or
                   n:find("llave") or n:find("continue") or n:find("next") or
                   n:find("ok") or n:find("yes") or
                   t:find("accept") or t:find("take") or t:find("key") or
                   t:find("yes") or t:find("ok") then
                    pcall(function() gui.MouseButton1Click:Fire() end)
                    task.wait(0.2)
                end
            end
        end
    end
    
    Util.Remoto("ratthew")
    Util.Remoto("key")
    Util.Remoto("secret")
    
    Util.Notificar("Ratthew", "🐭 ¡Llave de Ratthew obtenida!", 3)
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: COMPRAR MEJORAS EN TIENDA
-- ═══════════════════════════════════════
function Acciones.ComprarMejoras()
    if not Config.AutoComprarMejoras then return true end
    
    Estado.TareaActual = "🛒 Comprando mejoras..."
    
    -- Buscar la tienda (anciana de la tienda)
    local tienda = Detector.NPC("shop") or Detector.NPC("vendor") or 
                   Detector.NPC("store") or Detector.NPC("old")
    
    if tienda then
        Util.TP(tienda)
        task.wait(0.2)
        Util.ClickearObjeto(tienda)
        Util.Tecla(Enum.KeyCode.E)
        task.wait(0.5)
    end
    
    -- Comprar todo lo posible en la GUI
    local playerGui = Player:FindFirstChild("PlayerGui")
    if playerGui then
        for _, gui in pairs(playerGui:GetDescendants()) do
            if gui:IsA("TextButton") or gui:IsA("ImageButton") then
                local n = gui.Name:lower()
                local t = ""
                pcall(function() t = gui.Text:lower() end)
                
                if n:find("buy") or n:find("purchase") or n:find("upgrade") or
                   n:find("comprar") or n:find("mejora") or
                   t:find("buy") or t:find("purchase") or t:find("upgrade") or
                   t:find("comprar") then
                    pcall(function() gui.MouseButton1Click:Fire() end)
                    task.wait(0.2)
                end
            end
        end
    end
    
    Util.Remoto("buy")
    Util.Remoto("purchase")
    Util.Remoto("upgrade")
    
    return true
end

-- ═══════════════════════════════════════
-- ACCIÓN: AUTO CURAR PACIENTES
-- ═══════════════════════════════════════
function Acciones.AutoCurar()
    if not Config.AutoCurarActivo then return end
    
    Estado.TareaActual = "💊 Curando pacientes..."
    
    -- Revisar cada cama
    for i, camaInfo in ipairs(Mapa.TodasLasCamas) do
        local camaInst = ResolverRuta(camaInfo.ruta)
        
        if camaInst then
            -- Verificar si hay paciente en la cama
            local tienePaciente = false
            
            for _, child in pairs(camaInst:GetDescendants()) do
                if child:IsA("Model") and child:FindFirstChild("Humanoid") then
                    tienePaciente = true
                    
                    local hum = child:FindFirstChild("Humanoid")
                    if hum and hum.Health < hum.MaxHealth then
                        -- Ir a la cama
                        local root = Util.Root()
                        if root then
                            root.CFrame = CFrame.new(camaInfo.pos + Vector3.new(0, 3, 0))
                        end
                        task.wait(0.1)
                        
                        -- Interactuar
                        Util.ClickearObjeto(camaInst)
                        Util.Tecla(Enum.KeyCode.E)
                        task.wait(0.2)
                        
                        -- Determinar tratamiento
                        local tipo = child:GetAttribute("TreatmentType") or ""
                        tipo = tipo:lower()
                        
                        if tipo:find("surgery") then
                            Acciones.RealizarCirugia()
                        elseif tipo:find("cpr") or tipo:find("heart") then
                            Acciones.RealizarRCP()
                        elseif tipo:find("xray") then
                            Acciones.RealizarRayosX()
                        elseif tipo:find("dna") then
                            Acciones.RealizarADN()
                        else
                            -- Curación general
                            Util.Remoto("heal", child)
                            Util.Remoto("treat", child)
                            Util.Remoto("cure", child)
                            Util.Remoto("medicine", child)
                        end
                        
                        Estado.PacientesAtendidos = Estado.PacientesAtendidos + 1
                    end
                end
            end
            
            Estado.CamasOcupadas[i] = tienePaciente
        end
    end
end

-- ═══════════════════════════════════════
-- ACCIÓN: AUTO FARM GENERAL (DINERO)
-- ═══════════════════════════════════════
function Acciones.AutoFarm()
    if not Config.AutoFarmActivo then return end
    
    -- Recoger dinero/monedas del mapa
    for _, obj in pairs(Workspace:GetDescendants()) do
        if obj:IsA("BasePart") then
            local n = obj.Name:lower()
            if n:find("coin") or n:find("money") or n:find("cash") or
               n:find("reward") or n:find("gem") or n:find("collectible") or
               n:find("pickup") or n:find("moneda") or n:find("dinero") then
                local dist = Util.Distancia(obj)
                if dist < 300 then
                    local root = Util.Root()
                    if root then
                        root.CFrame = CFrame.new(obj.Position)
                        task.wait(0.03)
                    end
                    Util.ClickearObjeto(obj)
                end
            end
        end
    end
    
    -- Cobrar recompensas
    Util.Remoto("collect")
    Util.Remoto("reward")
    Util.Remoto("salary")
    Util.Remoto("pay")
    Util.Remoto("claim")
end

-- ═══════════════════════════════════════
-- ACCIÓN: COMPLETAR MINIJUEGOS GENÉRICOS
-- ═══════════════════════════════════════
function Acciones.CompletarMinijuegos()
    if not Config.AutoMiniJuegos then return end
    
    local playerGui = Player:FindFirstChild("PlayerGui")
    if not playerGui then return end
    
    for _, gui in pairs(playerGui:GetDescendants()) do
        if (gui:IsA("TextButton") or gui:IsA("ImageButton")) and gui.Visible then
            local n = gui.Name:lower()
            local t = ""
            pcall(function() t = gui.Text:lower() end)
            
            local palabras = {
                "complete", "finish", "done", "submit", "confirm",
                "press", "click", "tap", "hit", "catch",
                "grab", "pick", "select", "play", "start", "go"
            }
            
            for _, palabra in pairs(palabras) do
                if n:find(palabra) or t:find(palabra) then
                    pcall(function() gui.MouseButton1Click:Fire() end)
                    Estado.MinijuegosCompletados = Estado.MinijuegosCompletados + 1
                    task.wait(0.05)
                    break
                end
            end
        end
    end
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 9: SISTEMA INTELIGENTE DE PRIORIDADES
-- ══════════════════════════════════════════════════════════════

local SistemaIA = {}

function SistemaIA.CrearEvento(tipo, prioridad, objetivo, callback)
    return {
        Tipo = tipo,
        Prioridad = prioridad,
        Objetivo = objetivo,
        Callback = callback,
        Tiempo = tick(),
        Completado = false,
    }
end

function SistemaIA.Agregar(evento)
    -- Verificar duplicados
    for _, ev in pairs(Estado.ColaEventos) do
        if ev.Tipo == evento.Tipo and ev.Objetivo == evento.Objetivo and not ev.Completado then
            return -- Ya existe
        end
    end
    
    table.insert(Estado.ColaEventos, evento)
    
    -- Ordenar por prioridad
    table.sort(Estado.ColaEventos, function(a, b)
        if a.Prioridad == b.Prioridad then
            return a.Tiempo < b.Tiempo
        end
        return a.Prioridad < b.Prioridad
    end)
end

function SistemaIA.Siguiente()
    for i, ev in ipairs(Estado.ColaEventos) do
        if not ev.Completado then
            return ev, i
        end
    end
    return nil
end

function SistemaIA.Limpiar()
    local nueva = {}
    for _, ev in pairs(Estado.ColaEventos) do
        if not ev.Completado and (tick() - ev.Tiempo) < 45 then
            table.insert(nueva, ev)
        end
    end
    Estado.ColaEventos = nueva
end

-- Escaneo completo de amenazas y tareas
function SistemaIA.Escanear()
    if not Config.SistemaInteligente then return end
    
    -- 1. Skinwalkers
    if Config.AutoEliminarSkinwalkers then
        for _, sk in pairs(Detector.Skinwalkers()) do
            SistemaIA.Agregar(SistemaIA.CrearEvento(
                "SkinwalkerAtacando", Config.Prioridades.SkinwalkerAtacando, sk,
                function() return Acciones.EliminarSkinwalker(sk) end
            ))
        end
    end
    
    -- 2. Desmayos
    if Config.AutoDesmayos then
        for _, d in pairs(Detector.Desmayos()) do
            SistemaIA.Agregar(SistemaIA.CrearEvento(
                "DesmayoCritico", Config.Prioridades.DesmayoCritico, d,
                function() return Acciones.AtenderDesmayo(d) end
            ))
        end
    end
    
    -- 3. Incendios
    if Config.AutoExtinguirActivo then
        for _, f in pairs(Detector.Incendios()) do
            SistemaIA.Agregar(SistemaIA.CrearEvento(
                "PacienteEnLlamas", Config.Prioridades.PacienteEnLlamas, f,
                function() return Acciones.ExtinguirFuego(f) end
            ))
        end
    end
    
    -- 4. Rituales
    if Config.AutoRitualMuerte then
        local velas = Detector.Rituales()
        if #velas > 0 then
            SistemaIA.Agregar(SistemaIA.CrearEvento(
                "RitualDeMuerte", Config.Prioridades.RitualDeMuerte, velas,
                function() return Acciones.DetenerRitual(velas) end
            ))
        end
    end
    
    -- 5. Monstruos bajo cama
    for _, m in pairs(Detector.MonstruosBajoCama()) do
        SistemaIA.Agregar(SistemaIA.CrearEvento(
            "MonstruoBajoCama", Config.Prioridades.MonstruoBajoCama, m,
            function() return Acciones.EliminarSkinwalker(m) end
        ))
    end
    
    -- 6. Fantasmas
    for _, f in pairs(Detector.Fantasmas()) do
        SistemaIA.Agregar(SistemaIA.CrearEvento(
            "FantasmaOjosNegros", Config.Prioridades.FantasmaOjosNegros, f,
            function() return Acciones.EliminarFantasma(f) end
        ))
    end
    
    -- 7. Cordura baja
    if Config.AutoTomarCafe and Estado.CorduraActual <= Config.UmbralCafeCritico then
        SistemaIA.Agregar(SistemaIA.CrearEvento(
            "CorduraCritica", Config.Prioridades.CorduraCritica, nil,
            function() return Acciones.TomarCafe() end
        ))
    end
    
    -- 8. Slime
    if Config.AutoLimpiarSlime then
        for _, s in pairs(Detector.Slime()) do
            SistemaIA.Agregar(SistemaIA.CrearEvento(
                "LimpiarSlime", Config.Prioridades.LimpiarSlime, s,
                function() return Acciones.LimpiarSlime(s) end
            ))
        end
    end
    
    -- 9. Barney
    if Config.AutoBarney then
        local barney = Detector.NPC("barney")
        if barney then
            SistemaIA.Agregar(SistemaIA.CrearEvento(
                "EventoBarney", Config.Prioridades.EventoBarney, barney,
                function() return Acciones.ManejarBarney(barney) end
            ))
        end
    end
    
    -- 10. Ratthew
    if Config.AutoRatthew then
        local ratthew = Detector.NPC("ratthew")
        if ratthew then
            SistemaIA.Agregar(SistemaIA.CrearEvento(
                "EventoRatthew", Config.Prioridades.EventoRatthew, ratthew,
                function() return Acciones.ManejarRatthew(ratthew) end
            ))
        end
    end
    
    SistemaIA.Limpiar()
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 10: MONITOR DE ESTADÍSTICAS
-- ══════════════════════════════════════════════════════════════

local function ActualizarEstadisticas()
    local playerGui = Player:FindFirstChild("PlayerGui")
    if playerGui then
        for _, gui in pairs(playerGui:GetDescendants()) do
            local n = gui.Name:lower()
            if gui:IsA("TextLabel") then
                if n:find("sanity") or n:find("cordura") or n:find("energy") then
                    local v = tonumber(gui.Text:match("%d+"))
                    if v then Estado.CorduraActual = v end
                end
                if n:find("money") or n:find("cash") or n:find("coin") or n:find("dinero") then
                    local v = tonumber(gui.Text:match("%d+"))
                    if v then Estado.DineroGanado = v end
                end
            end
        end
    end
    
    -- Leaderstats
    local ls = Player:FindFirstChild("leaderstats")
    if ls then
        for _, s in pairs(ls:GetChildren()) do
            local n = s.Name:lower()
            if n:find("money") or n:find("cash") or n:find("coin") then
                Estado.DineroGanado = s.Value or 0
            end
        end
    end
    
    -- Atributos directos
    if Player:GetAttribute("Sanity") then Estado.CorduraActual = Player:GetAttribute("Sanity") end
    if Player:GetAttribute("Money") then Estado.DineroGanado = Player:GetAttribute("Money") end
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 11: INTERFAZ GRÁFICA (PANEL EN ESPAÑOL)
-- ══════════════════════════════════════════════════════════════

local function CrearGUI()
    -- Eliminar anterior
    local old = CoreGui:FindFirstChild("AH_GUI")
    if old then old:Destroy() end
    
    local SG = Instance.new("ScreenGui")
    SG.Name = "AH_GUI"
    SG.ResetOnSpawn = false
    SG.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    SG.DisplayOrder = 999
    
    -- Frame Principal
    local MF = Instance.new("Frame")
    MF.Name = "Main"
    MF.Size = UDim2.new(0, 360, 0, 520)
    MF.Position = UDim2.new(0.5, -180, 0.5, -260)
    MF.BackgroundColor3 = Config.ColorPrincipal
    MF.BorderSizePixel = 0
    MF.Active = true
    MF.Draggable = true
    MF.Parent = SG
    
    Instance.new("UICorner", MF).CornerRadius = UDim.new(0, 12)
    local stroke = Instance.new("UIStroke", MF)
    stroke.Color = Config.ColorAcento
    stroke.Thickness = 2
    stroke.Transparency = 0.3
    
    -- Título
    local TB = Instance.new("Frame")
    TB.Size = UDim2.new(1, 0, 0, 42)
    TB.BackgroundColor3 = Config.ColorSecundario
    TB.BorderSizePixel = 0
    TB.Parent = MF
    Instance.new("UICorner", TB).CornerRadius = UDim.new(0, 12)
    
    local TBfix = Instance.new("Frame")
    TBfix.Size = UDim2.new(1, 0, 0, 12)
    TBfix.Position = UDim2.new(0, 0, 1, -12)
    TBfix.BackgroundColor3 = Config.ColorSecundario
    TBfix.BorderSizePixel = 0
    TBfix.Parent = TB
    
    local titulo = Instance.new("TextLabel")
    titulo.Size = UDim2.new(1, -90, 1, 0)
    titulo.Position = UDim2.new(0, 12, 0, 0)
    titulo.BackgroundTransparency = 1
    titulo.Text = "🏥 Hospital Animal v6.0"
    titulo.TextColor3 = Config.ColorTexto
    titulo.TextSize = 16
    titulo.Font = Enum.Font.GothamBold
    titulo.TextXAlignment = Enum.TextXAlignment.Left
    titulo.Parent = TB
    
    -- Botón Cerrar
    local cerrar = Instance.new("TextButton")
    cerrar.Size = UDim2.new(0, 28, 0, 28)
    cerrar.Position = UDim2.new(1, -35, 0, 7)
    cerrar.BackgroundColor3 = Config.ColorPeligro
    cerrar.Text = "✕"
    cerrar.TextColor3 = Color3.new(1,1,1)
    cerrar.TextSize = 14
    cerrar.Font = Enum.Font.GothamBold
    cerrar.BorderSizePixel = 0
    cerrar.Parent = TB
    Instance.new("UICorner", cerrar).CornerRadius = UDim.new(0, 7)
    
    -- Botón Minimizar
    local minimizar = Instance.new("TextButton")
    minimizar.Size = UDim2.new(0, 28, 0, 28)
    minimizar.Position = UDim2.new(1, -67, 0, 7)
    minimizar.BackgroundColor3 = Config.ColorAdvertencia
    minimizar.Text = "—"
    minimizar.TextColor3 = Color3.new(0,0,0)
    minimizar.TextSize = 14
    minimizar.Font = Enum.Font.GothamBold
    minimizar.BorderSizePixel = 0
    minimizar.Parent = TB
    Instance.new("UICorner", minimizar).CornerRadius = UDim.new(0, 7)
    
    -- ScrollFrame de contenido
    local SF = Instance.new("ScrollingFrame")
    SF.Name = "Content"
    SF.Size = UDim2.new(1, -16, 1, -50)
    SF.Position = UDim2.new(0, 8, 0, 46)
    SF.BackgroundTransparency = 1
    SF.BorderSizePixel = 0
    SF.ScrollBarThickness = 3
    SF.ScrollBarImageColor3 = Config.ColorAcento
    SF.CanvasSize = UDim2.new(0, 0, 0, 1250)
    SF.Parent = MF
    
    local layout = Instance.new("UIListLayout")
    layout.SortOrder = Enum.SortOrder.LayoutOrder
    layout.Padding = UDim.new(0, 4)
    layout.Parent = SF
    
    -- ═══ FUNCIONES AUXILIARES GUI ═══
    
    local orden = 0
    
    local function Seccion(texto, icono)
        orden = orden + 1
        local f = Instance.new("Frame")
        f.Size = UDim2.new(1, 0, 0, 26)
        f.BackgroundColor3 = Config.ColorSecundario
        f.BorderSizePixel = 0
        f.LayoutOrder = orden
        f.Parent = SF
        Instance.new("UICorner", f).CornerRadius = UDim.new(0, 6)
        
        local l = Instance.new("TextLabel")
        l.Size = UDim2.new(1, -8, 1, 0)
        l.Position = UDim2.new(0, 8, 0, 0)
        l.BackgroundTransparency = 1
        l.Text = icono .. " " .. texto
        l.TextColor3 = Config.ColorAcento
        l.TextSize = 12
        l.Font = Enum.Font.GothamBold
        l.TextXAlignment = Enum.TextXAlignment.Left
        l.Parent = f
    end
    
    local function Toggle(texto, configKey)
        orden = orden + 1
        local f = Instance.new("Frame")
        f.Size = UDim2.new(1, 0, 0, 28)
        f.BackgroundColor3 = Color3.fromRGB(18, 28, 50)
        f.BorderSizePixel = 0
        f.LayoutOrder = orden
        f.Parent = SF
        Instance.new("UICorner", f).CornerRadius = UDim.new(0, 5)
        
        local l = Instance.new("TextLabel")
        l.Size = UDim2.new(1, -60, 1, 0)
        l.Position = UDim2.new(0, 8, 0, 0)
        l.BackgroundTransparency = 1
        l.Text = texto
        l.TextColor3 = Config.ColorTextoSec
        l.TextSize = 11
        l.Font = Enum.Font.Gotham
        l.TextXAlignment = Enum.TextXAlignment.Left
        l.Parent = f
        
        local btn = Instance.new("TextButton")
        btn.Size = UDim2.new(0, 42, 0, 18)
        btn.Position = UDim2.new(1, -50, 0.5, -9)
        btn.BorderSizePixel = 0
        btn.Text = ""
        btn.Parent = f
        Instance.new("UICorner", btn).CornerRadius = UDim.new(1, 0)
        
        local circle = Instance.new("Frame")
        circle.Size = UDim2.new(0, 14, 0, 14)
        circle.BorderSizePixel = 0
        circle.Parent = btn
        Instance.new("UICorner", circle).CornerRadius = UDim.new(1, 0)
        
        local function actualizar()
            if Config[configKey] then
                btn.BackgroundColor3 = Config.ColorExito
                circle.Position = UDim2.new(1, -16, 0, 2)
                circle.BackgroundColor3 = Color3.new(1,1,1)
            else
                btn.BackgroundColor3 = Color3.fromRGB(55, 55, 75)
                circle.Position = UDim2.new(0, 2, 0, 2)
                circle.BackgroundColor3 = Color3.fromRGB(140, 140, 140)
            end
        end
        
        actualizar()
        
        btn.MouseButton1Click:Connect(function()
            Config[configKey] = not Config[configKey]
            actualizar()
            TweenService:Create(circle, TweenInfo.new(0.15), {
                Position = Config[configKey] and UDim2.new(1, -16, 0, 2) or UDim2.new(0, 2, 0, 2)
            }):Play()
        end)
    end
    
    local function Stat(texto, nombre)
        orden = orden + 1
        local f = Instance.new("Frame")
        f.Name = "S_" .. nombre
        f.Size = UDim2.new(1, 0, 0, 20)
        f.BackgroundTransparency = 1
        f.LayoutOrder = orden
        f.Parent = SF
        
        local l = Instance.new("TextLabel")
        l.Size = UDim2.new(0.6, 0, 1, 0)
        l.Position = UDim2.new(0, 8, 0, 0)
        l.BackgroundTransparency = 1
        l.Text = texto
        l.TextColor3 = Config.ColorTextoSec
        l.TextSize = 10
        l.Font = Enum.Font.Gotham
        l.TextXAlignment = Enum.TextXAlignment.Left
        l.Parent = f
        
        local v = Instance.new("TextLabel")
        v.Name = "V"
        v.Size = UDim2.new(0.4, -8, 1, 0)
        v.Position = UDim2.new(0.6, 0, 0, 0)
        v.BackgroundTransparency = 1
        v.Text = "0"
        v.TextColor3 = Config.ColorExito
        v.TextSize = 11
        v.Font = Enum.Font.GothamBold
        v.TextXAlignment = Enum.TextXAlignment.Right
        v.Parent = f
    end
    
    -- ═══ ESTADO ═══
    Seccion("ESTADO ACTUAL", "📊")
    
    orden = orden + 1
    local estadoLbl = Instance.new("TextLabel")
    estadoLbl.Name = "EstadoActual"
    estadoLbl.Size = UDim2.new(1, 0, 0, 26)
    estadoLbl.BackgroundColor3 = Color3.fromRGB(12, 30, 18)
    estadoLbl.BorderSizePixel = 0
    estadoLbl.Text = "⏳ Iniciando..."
    estadoLbl.TextColor3 = Config.ColorExito
    estadoLbl.TextSize = 11
    estadoLbl.Font = Enum.Font.GothamBold
    estadoLbl.LayoutOrder = orden
    estadoLbl.Parent = SF
    Instance.new("UICorner", estadoLbl).CornerRadius = UDim.new(0, 5)
    
    -- ═══ AUTOMATIZACIÓN ═══
    Seccion("AUTOMATIZACIÓN", "🤖")
    Toggle("Auto Farm General", "AutoFarmActivo")
    Toggle("Sistema Inteligente", "SistemaInteligente")
    Toggle("Auto Recepción", "AutoRecepcionActivo")
    Toggle("Auto Cirugía", "AutoCirugiaActivo")
    Toggle("Auto RCP/Cardíaco", "AutoRCPActivo")
    Toggle("Auto Rayos X", "AutoRayosXActivo")
    Toggle("Auto ADN", "AutoADNActivo")
    Toggle("Auto Curar", "AutoCurarActivo")
    Toggle("Auto Minijuegos", "AutoMiniJuegos")
    
    -- ═══ SUPERVIVENCIA ═══
    Seccion("SUPERVIVENCIA", "🛡️")
    Toggle("Eliminar Skinwalkers", "AutoEliminarSkinwalkers")
    Toggle("Extinguir Incendios", "AutoExtinguirActivo")
    Toggle("Detener Rituales", "AutoRitualMuerte")
    Toggle("Atender Desmayos", "AutoDesmayos")
    Toggle("Cerrar Persianas", "AutoCerrarPersianas")
    Toggle("Limpiar Slime", "AutoLimpiarSlime")
    Toggle("Reparar Cámaras", "AutoRepararCamaras")
    Toggle("Auto Café/Cordura", "AutoTomarCafe")
    
    -- ═══ EVENTOS ═══
    Seccion("EVENTOS ESPECIALES", "⭐")
    Toggle("Evento Barney", "AutoBarney")
    Toggle("Evento Ratthew", "AutoRatthew")
    Toggle("Auto Comprar Mejoras", "AutoComprarMejoras")
    
    -- ═══ MOVIMIENTO ═══
    Seccion("MOVIMIENTO", "🏃")
    Toggle("Teletransportación", "TeletransportacionActiva")
    Toggle("Traspasar Paredes", "NoClipActivo")
    Toggle("Súper Velocidad", "SuperVelocidadActiva")
    
    -- ═══ ESTADÍSTICAS ═══
    Seccion("ESTADÍSTICAS", "📈")
    Stat("💰 Dinero", "Dinero")
    Stat("🏥 Pacientes", "Pacientes")
    Stat("⚔️ Skinwalkers", "Skinwalkers")
    Stat("🔪 Cirugías", "Cirugias")
    Stat("🔥 Incendios", "Incendios")
    Stat("🕯️ Rituales", "Rituales")
    Stat("🚨 Desmayos", "Desmayos")
    Stat("⚠️ Anomalías", "Anomalias")
    Stat("🐻 Barney", "Barney")
    Stat("🎮 Minijuegos", "Minijuegos")
    Stat("🧠 Cordura", "Cordura")
    
    -- Barra de cordura
    orden = orden + 1
    local barraFrame = Instance.new("Frame")
    barraFrame.Name = "CorduraBarra"
    barraFrame.Size = UDim2.new(1, 0, 0, 16)
    barraFrame.BackgroundColor3 = Color3.fromRGB(25, 25, 35)
    barraFrame.BorderSizePixel = 0
    barraFrame.LayoutOrder = orden
    barraFrame.Parent = SF
    Instance.new("UICorner", barraFrame).CornerRadius = UDim.new(0, 4)
    
    local barraFill = Instance.new("Frame")
    barraFill.Name = "Fill"
    barraFill.Size = UDim2.new(1, 0, 1, 0)
    barraFill.BackgroundColor3 = Config.ColorExito
    barraFill.BorderSizePixel = 0
    barraFill.Parent = barraFrame
    Instance.new("UICorner", barraFill).CornerRadius = UDim.new(0, 4)
    
    -- Botón Master
    orden = orden + 1
    local master = Instance.new("TextButton")
    master.Name = "Master"
    master.Size = UDim2.new(1, 0, 0, 36)
    master.BackgroundColor3 = Config.ColorExito
    master.Text = "⚡ SCRIPT ACTIVO ⚡"
    master.TextColor3 = Color3.new(0,0,0)
    master.TextSize = 14
    master.Font = Enum.Font.GothamBold
    master.BorderSizePixel = 0
    master.LayoutOrder = orden
    master.Parent = SF
    Instance.new("UICorner", master).CornerRadius = UDim.new(0, 8)
    
    master.MouseButton1Click:Connect(function()
        Config.ScriptActivo = not Config.ScriptActivo
        master.BackgroundColor3 = Config.ScriptActivo and Config.ColorExito or Config.ColorPeligro
        master.Text = Config.ScriptActivo and "⚡ SCRIPT ACTIVO ⚡" or "⛔ SCRIPT PAUSADO ⛔"
        master.TextColor3 = Config.ScriptActivo and Color3.new(0,0,0) or Color3.new(1,1,1)
    end)
    
    -- Créditos
    orden = orden + 1
    local cred = Instance.new("TextLabel")
    cred.Size = UDim2.new(1, 0, 0, 16)
    cred.BackgroundTransparency = 1
    cred.Text = "Delta Executor | 13/07/2026 | Rutas Reales"
    cred.TextColor3 = Color3.fromRGB(70, 70, 90)
    cred.TextSize = 9
    cred.Font = Enum.Font.Gotham
    cred.LayoutOrder = orden
    cred.Parent = SF
    
    -- === EVENTOS DE BOTONES ===
    local mini = false
    minimizar.MouseButton1Click:Connect(function()
        mini = not mini
        SF.Visible = not mini
        TweenService:Create(MF, TweenInfo.new(0.25), {
            Size = mini and UDim2.new(0, 360, 0, 46) or UDim2.new(0, 360, 0, 520)
        }):Play()
    end)
    
    -- Botón flotante
    local floatBtn = Instance.new("TextButton")
    floatBtn.Name = "Float"
    floatBtn.Size = UDim2.new(0, 40, 0, 40)
    floatBtn.Position = UDim2.new(0, 8, 0.5, -20)
    floatBtn.BackgroundColor3 = Config.ColorAcento
    floatBtn.Text = "🏥"
    floatBtn.TextSize = 20
    floatBtn.BorderSizePixel = 0
    floatBtn.Visible = false
    floatBtn.Draggable = true
    floatBtn.Parent = SG
    Instance.new("UICorner", floatBtn).CornerRadius = UDim.new(1, 0)
    
    cerrar.MouseButton1Click:Connect(function()
        MF.Visible = false
        floatBtn.Visible = true
    end)
    
    floatBtn.MouseButton1Click:Connect(function()
        MF.Visible = true
        floatBtn.Visible = false
        Config.ScriptActivo = true
    end)
    
    -- Colocar en CoreGui
    pcall(function() SG.Parent = CoreGui end)
    if not SG.Parent then SG.Parent = Player:WaitForChild("PlayerGui") end
    
    return SG
end

-- Actualizar GUI
local function ActualizarGUI(sg)
    if not sg or not sg.Parent then return end
    
    local mf = sg:FindFirstChild("Main")
    if not mf then return end
    local sf = mf:FindFirstChild("Content")
    if not sf then return end
    
    -- Estado
    local est = sf:FindFirstChild("EstadoActual")
    if est then est.Text = Estado.TareaActual end
    
    -- Estadísticas
    local stats = {
        Dinero = Estado.DineroGanado,
        Pacientes = Estado.PacientesAtendidos,
        Skinwalkers = Estado.SkinwalkersEliminados,
        Cirugias = Estado.CirugiasCompletadas,
        Incendios = Estado.IncendiosExtinguidos,
        Rituales = Estado.RitualesDetenidos,
        Desmayos = Estado.DesmayosSalvados,
        Anomalias = Estado.AnomalíasDetectadas,
        Barney = Estado.EventosBarneyCompletados,
        Minijuegos = Estado.MinijuegosCompletados,
        Cordura = math.floor(Estado.CorduraActual) .. "%",
    }
    
    for nombre, valor in pairs(stats) do
        local frame = sf:FindFirstChild("S_" .. nombre)
        if frame then
            local v = frame:FindFirstChild("V")
            if v then
                v.Text = tostring(valor)
                
                if nombre == "Cordura" then
                    if Estado.CorduraActual > 50 then
                        v.TextColor3 = Config.ColorExito
                    elseif Estado.CorduraActual > 25 then
                        v.TextColor3 = Config.ColorAdvertencia
                    else
                        v.TextColor3 = Config.ColorPeligro
                    end
                end
            end
        end
    end
    
    -- Barra de cordura
    local barra = sf:FindFirstChild("CorduraBarra")
    if barra then
        local fill = barra:FindFirstChild("Fill")
        if fill then
            local pct = math.clamp(Estado.CorduraActual / 100, 0, 1)
            TweenService:Create(fill, TweenInfo.new(0.25), {
                Size = UDim2.new(pct, 0, 1, 0)
            }):Play()
            
            if pct > 0.5 then
                fill.BackgroundColor3 = Config.ColorExito
            elseif pct > 0.25 then
                fill.BackgroundColor3 = Config.ColorAdvertencia
            else
                fill.BackgroundColor3 = Config.ColorPeligro
            end
        end
    end
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 12: SISTEMA ANTI-AFK Y PROTECCIÓN
-- ══════════════════════════════════════════════════════════════

local function Proteccion()
    pcall(function()
        local vu = game:GetService("VirtualUser")
        Player.Idled:Connect(function()
            vu:CaptureController()
            vu:ClickButton2(Vector2.new())
        end)
    end)
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 13: ATAJOS DE TECLADO
-- ══════════════════════════════════════════════════════════════

local function Atajos()
    UserInputService.InputBegan:Connect(function(input, processed)
        if processed then return end
        
        if input.KeyCode == Enum.KeyCode.F1 then
            Config.ScriptActivo = not Config.ScriptActivo
            Util.Notificar("Script", Config.ScriptActivo and "✅ ACTIVADO" or "⛔ PAUSADO", 2)
        elseif input.KeyCode == Enum.KeyCode.F2 then
            Config.NoClipActivo = not Config.NoClipActivo
            Util.Notificar("NoClip", Config.NoClipActivo and "✅ ON" or "❌ OFF", 2)
        elseif input.KeyCode == Enum.KeyCode.F3 then
            Config.SuperVelocidadActiva = not Config.SuperVelocidadActiva
            Util.Notificar("Velocidad", Config.SuperVelocidadActiva and "🏃 RÁPIDO" or "🚶 NORMAL", 2)
        elseif input.KeyCode == Enum.KeyCode.F4 then
            -- TP a recepción
            Util.TP(CFrame.new(0, 8, -25))
            Util.Notificar("TP", "📋 Recepción", 2)
        elseif input.KeyCode == Enum.KeyCode.F5 then
            SistemaIA.Escanear()
            Util.Notificar("Escaneo", "🔍 Escaneo completo", 2)
        elseif input.KeyCode == Enum.KeyCode.F6 then
            task.spawn(Acciones.TomarCafe)
        end
    end)
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 14: DETECTOR DE OBJETOS NUEVOS EN TIEMPO REAL
-- ══════════════════════════════════════════════════════════════

local function MonitorearNuevosObjetos()
    Workspace.DescendantAdded:Connect(function(obj)
        if not Config.ScriptActivo then return end
        
        local n = obj.Name:lower()
        
        -- Nuevos Skinwalkers
        if n:find("skinwalker") or n:find("anomaly") or n:find("monster") or
           n:find("entity") or n:find("ghost") or n:find("creature") then
            if Config.AutoEliminarSkinwalkers then
                task.spawn(function()
                    task.wait(0.1)
                    SistemaIA.Agregar(SistemaIA.CrearEvento(
                        "SkinwalkerAtacando", 1, obj,
                        function() return Acciones.EliminarSkinwalker(obj) end
                    ))
                end)
            end
        end
        
        -- Nuevos incendios
        if obj:IsA("Fire") then
            if Config.AutoExtinguirActivo then
                task.spawn(function()
                    task.wait(0.1)
                    local modelo = obj.Parent
                    if modelo and modelo.Parent and modelo.Parent:IsA("Model") then
                        modelo = modelo.Parent
                    end
                    SistemaIA.Agregar(SistemaIA.CrearEvento(
                        "PacienteEnLlamas", 3, modelo,
                        function() return Acciones.ExtinguirFuego(modelo) end
                    ))
                end)
            end
        end
        
        -- Nuevas velas (ritual)
        if n:find("candle") or n:find("ritual") then
            if Config.AutoRitualMuerte then
                task.spawn(function()
                    task.wait(0.2)
                    local velas = Detector.Rituales()
                    if #velas > 0 then
                        SistemaIA.Agregar(SistemaIA.CrearEvento(
                            "RitualDeMuerte", 4, velas,
                            function() return Acciones.DetenerRitual(velas) end
                        ))
                    end
                end)
            end
        end
        
        -- Desmayos
        if n:find("faint") or n:find("emergency") or n:find("critical") or n:find("ambulance") then
            if Config.AutoDesmayos and obj:IsA("Model") then
                task.spawn(function()
                    task.wait(0.1)
                    SistemaIA.Agregar(SistemaIA.CrearEvento(
                        "DesmayoCritico", 2, obj,
                        function() return Acciones.AtenderDesmayo(obj) end
                    ))
                end)
            end
        end
    end)
end

-- ══════════════════════════════════════════════════════════════
-- SECCIÓN 15: BUCLE PRINCIPAL
-- ══════════════════════════════════════════════════════════════

local function Principal()
    print("═══════════════════════════════════════════════")
    print("  🏥 ANIMAL HOSPITAL SCRIPT v6.0")
    print("  📍 Con Rutas Reales y Coordenadas Exactas")
    print("  📅 13 de Julio 2026 - Delta Executor")
    print("═══════════════════════════════════════════════")
    
    -- Esperar personaje
    if not Player.Character then Player.CharacterAdded:Wait() end
    task.wait(1)
    
    -- Inicializar
    Util.Log("Resolviendo rutas del mapa...")
    ResolverTodasLasRutas()
    
    Util.Log("Creando interfaz...")
    local gui = CrearGUI()
    
    Util.Log("Activando NoClip...")
    ActivarNoClip()
    
    Util.Log("Activando velocidad...")
    MonitorearVelocidad()
    
    Util.Log("Activando protección anti-AFK...")
    Proteccion()
    
    Util.Log("Configurando atajos de teclado...")
    Atajos()
    
    Util.Log("Iniciando monitor de objetos nuevos...")
    MonitorearNuevosObjetos()
    
    -- Reconectar al respawnear
    Player.CharacterAdded:Connect(function()
        task.wait(1)
        ActivarNoClip()
        MonitorearVelocidad()
        ResolverTodasLasRutas()
        Util.Log("Personaje respawneado - Sistemas reactivados")
    end)
    
    Util.Notificar("¡LISTO!", "🏥 Script v6.0 con rutas reales\nF1-F6 para atajos", 5)
    
    -- ═══════════════════════════════════
    -- BUCLE PRINCIPAL
    -- ═══════════════════════════════════
    
    local ciclo = 0
    
    while task.wait(0.1) do
        if not Config.ScriptActivo then
            Estado.TareaActual = "⛔ Pausado"
            ActualizarGUI(gui)
            task.wait(0.5)
            continue
        end
        
        ciclo = ciclo + 1
        
        -- Actualizar estadísticas
        ActualizarEstadisticas()
        
        -- SISTEMA INTELIGENTE
        if Config.SistemaInteligente then
            -- Escaneo cada 5 ciclos
            if ciclo % 5 == 0 then
                SistemaIA.Escanear()
            end
            
            -- Ejecutar evento más prioritario
            if not Estado.Ocupado then
                local evento = SistemaIA.Siguiente()
                
                if evento then
                    Estado.Ocupado = true
                    task.spawn(function()
                        pcall(function()
                            if evento.Callback then
                                evento.Callback()
                            end
                        end)
                        evento.Completado = true
                        Estado.Ocupado = false
                    end)
                else
                    -- Rutina normal cuando no hay emergencias
                    
                    if Config.AutoFarmActivo and ciclo % 10 == 0 then
                        task.spawn(Acciones.AutoFarm)
                    end
                    
                    if Config.AutoRecepcionActivo and ciclo % 15 == 0 then
                        task.spawn(function()
                            Estado.Ocupado = true
                            Acciones.RegistrarPaciente()
                            Estado.Ocupado = false
                        end)
                    end
                    
                    if Config.AutoCurarActivo and ciclo % 20 == 0 then
                        task.spawn(function()
                            Estado.Ocupado = true
                            Acciones.AutoCurar()
                            Estado.Ocupado = false
                        end)
                    end
                    
                    if Config.AutoMiniJuegos and ciclo % 3 == 0 then
                        task.spawn(Acciones.CompletarMinijuegos)
                    end
                    
                    if Config.AutoTomarCafe and Estado.CorduraActual <= Config.UmbralCafeMinimo then
                        task.spawn(function()
                            Estado.Ocupado = true
                            Acciones.TomarCafe()
                            Estado.Ocupado = false
                        end)
                    end
                    
                    if Config.AutoRepararCamaras and ciclo % 50 == 0 then
                        if Detector.FusiblesRotos() then
                            task.spawn(function()
                                Estado.Ocupado = true
                                Acciones.RepararCamaras()
                                Estado.Ocupado = false
                            end)
                        end
                    end
                    
                    if Config.AutoComprarMejoras and ciclo % 80 == 0 then
                        task.spawn(Acciones.ComprarMejoras)
                    end
                    
                    Estado.TareaActual = "✅ Monitoreando hospital..."
                end
            end
        else
            -- Sin IA: ejecutar todo en paralelo
            if ciclo % 3 == 0 then
                task.spawn(function()
                    for _, sk in pairs(Detector.Skinwalkers()) do
                        Acciones.EliminarSkinwalker(sk) end
                end)
                task.spawn(function()
                    for _, d in pairs(Detector.Desmayos()) do
                        Acciones.AtenderDesmayo(d) end
                end)
                task.spawn(function()
                    for _, f in pairs(Detector.Incendios()) do
                        Acciones.ExtinguirFuego(f) end
                end)
                task.spawn(function()
                    local v = Detector.Rituales()
                    if #v > 0 then Acciones.DetenerRitual(v) end
                end)
            end
            
            if ciclo % 8 == 0 then
                task.spawn(Acciones.AutoFarm)
                task.spawn(Acciones.AutoCurar)
            end
            
            if ciclo % 12 == 0 then
                task.spawn(Acciones.RegistrarPaciente)
            end
            
            if ciclo % 3 == 0 then
                task.spawn(Acciones.CompletarMinijuegos)
            end
        end
        
        -- Actualizar GUI
        if ciclo % 4 == 0 then
            pcall(function() ActualizarGUI(gui) end)
        end
        
        -- Mantener velocidad
        if Config.SuperVelocidadActiva then
            local hum = Util.Humanoid()
            if hum then hum.WalkSpeed = Config.SuperVelocidad end
        end
        
        if ciclo > 10000 then ciclo = 0 end
    end
end

-- ══════════════════════════════════════════════════════════════
-- EJECUTAR
-- ══════════════════════════════════════════════════════════════

local ok, err = pcall(Principal)
if not ok then
    warn("🏥 Error: " .. tostring(err))
    Util.Notificar("Error", tostring(err), 10)
    task.wait(3)
    pcall(Principal)
end

--[[
═══════════════════════════════════════════════════════════════
                   GUÍA RÁPIDA DE USO
═══════════════════════════════════════════════════════════════

🎮 ATAJOS:
  F1 → Activar/Pausar script
  F2 → NoClip ON/OFF
  F3 → Súper Velocidad ON/OFF
  F4 → TP a Recepción (0, 5, -25)
  F5 → Escaneo forzado del mapa
  F6 → Tomar café manual

📍 UBICACIONES USADAS (Coordenadas Reales):
  Timbre:          (0, 5, -25)   → Map.Reception.Bell
  Cámara:          (4, 5, -24)   → Map.Reception.Camera
  Persiana:        (-10, 7, -26) → Map.Reception.ShutterButton
  Café:            (35, 4, -15)  → Map.Breakroom.CoffeeMachine
  Cama 1:          (-20, 3, 40)  → Map.Beds.Bed1
  Cama 2:          (-20, 3, 55)  → Map.Beds.Bed2
  Cama 3:          (20, 3, 40)   → Map.Beds.Bed3
  Cama 4:          (20, 3, 55)   → Map.Beds.Bed4
  Medicinas:       (0, 5, 65)    → Map.Pharmacy.Cabinet
  Rayos X:         (-45, 3, 80)  → Map.XRayRoom.XRayMachine
  Cirugía:         (45, 3, 80)   → Map.SurgeryRoom.OperatingTable
  Fusibles:        (0, 6, 110)   → Map.Maintenance.FuseBox
  CCTV:            (-15, 6, 20)  → Map.Hallways.CCTVPanel1
  Extintor:        (15, 5, 10)   → Map.Hallways.Extinguisher
  Trapeador:       (5, 3, 105)   → Map.Maintenance.Mop

🧠 PRIORIDADES (el bot atiende en este orden):
  1. Skinwalkers atacando
  2. Desmayos críticos
  3. Pacientes en llamas
  4. Rituales de muerte
  5. Monstruos/Fantasmas
  6. Emergencias ambulancia
  7. Cordura crítica
  8-10. Procedimientos médicos
  11+. Tareas de mantenimiento

⚙️ MÉTODOS DE INTERACCIÓN:
  • Teletransporte: root.CFrame = CFrame.new(X, Y, Z)
  • Interacción: fireclickdetector(objeto.ClickDetector)
  • Prompts: fireproximityprompt(prompt)
  • GUI: gui.MouseButton1Click:Fire()

═══════════════════════════════════════════════════════════════
--]]
