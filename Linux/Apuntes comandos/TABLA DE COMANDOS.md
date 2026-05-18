
bc, python3 -m https.server 80, lsof -i:80, pwdx PID, tcpdump -i enp0s3 Captura.cap -v, xxd -ps -r, tshark, disown

```dataviewjs
const container = dv.container.createEl("div", { 
    style: "background: var(--background-secondary); padding: 15px; border-radius: 8px; border: 1px solid var(--interactive-accent); margin-bottom: 20px;" 
});

const input = container.createEl("input", {
    type: "text",
    placeholder: "🔍 CMD + comando",
    style: "width: 150%; padding: 10px; border-radius: 5px; border: 1px solid var(--background-modifier-border); background: var(--background-primary); color: var(--text-normal);"
});

const resultsArea = container.createEl("div");

input.addEventListener("input", async (e) => {
    const query = e.target.value.toLowerCase().trim();
    resultsArea.innerHTML = ""; 
    if (query.length < 2) return;

    const file = app.workspace.getActiveFile();
    const content = await app.vault.read(file);
    
    // Solo buscamos lo que esté entre etiquetas <table>
    const tables = content.match(/<table[\s\S]*?<\/table>/g);

    if (tables) {
        tables.forEach(tableHtml => {
            if (tableHtml.toLowerCase().includes(query)) {
                const div = resultsArea.createEl("div", { style: "margin-top: 15px;" });
                div.innerHTML = tableHtml;
                resultsArea.createEl("hr", { style: "margin: 15px 0; opacity: 0.2;" });
            }
        });
    }
});
```


<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #003366, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">[EMOTICONO] CMD [COMANDO]</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">[DESCRIPCIÓN CORTA DEL COMANDO]</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">[OPCIÓN]</td>
        <td style="padding: 10px 15px;">[DESCRIPCIÓN]</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">[EJEMPLO]</code></td>
      </tr>
      
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">[OPCIÓN]</td>
        <td style="padding: 10px 15px;">[DESCRIPCIÓN]</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">[EJEMPLO]</code></td>
      </tr>
    </tbody>
  </table>
</div>


<table style="border-collapse: collapse; width: 100%; font-family: sans-serif; margin-bottom: 20px; border: 1px solid #444;">
  <tr style="background-color: #1a1a1a;">
    <th colspan="3" style="padding: 12px; text-align: center; color: white; border-bottom: 2px solid #007acc;">
      <b>🎨 LEYENDA DE CATEGORÍAS Y COLORES</b>
    </th>
  </tr>
  <tr style="font-weight: bold; background-color: #252525;">
    <td style="padding: 8px; border: 1px solid #444; text-align: center;">Color</td>
    <td style="padding: 8px; border: 1px solid #444;">Categoría</td>
    <td style="padding: 8px; border: 1px solid #444;">Uso / Tipo de Comando</td>
  </tr>
  <tr>
    <td style="background-color: #004080; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Búsqueda / Info</td>
    <td style="padding: 8px; border: 1px solid #444;">Localizar archivos, lectura y ayuda (ej: ls, tldr, find, xxd).</td>
  </tr>
  <tr>
    <td style="background-color: #1b5e20; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Hackeo / Redes</td>
    <td style="padding: 8px; border: 1px solid #444;">Ataque, escaneo y tráfico (ej: nmap, airmon-ng, nc).</td>
  </tr>
  <tr>
    <td style="background-color: #00acc1; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Defensiva / Logs</td>
    <td style="padding: 8px; border: 1px solid #444;">Protección, firewalls y auditoría (ej: ufw, journalctl, iptables).</td>
  </tr>
  <tr>
    <td style="background-color: #b71c1c; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Peligro / Crítico</td>
    <td style="padding: 8px; border: 1px solid #444;">Borrado irreversible o cambios críticos (ej: rm, dd, shred).</td>
  </tr>
  <tr>
    <td style="background-color: #4a148c; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Permisos / Usuarios</td>
    <td style="padding: 8px; border: 1px solid #444;">Gestión de privilegios y cuentas (ej: chmod, sudo, chown).</td>
  </tr>
  <tr>
    <td style="background-color: #f48fb1; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Scripting / Filtros</td>
    <td style="padding: 8px; border: 1px solid #444;">Procesado de texto y automatización (ej: awk, sed, grep).</td>
  </tr>
  <tr>
    <td style="background-color: #333333; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Sistema / Gestión</td>
    <td style="padding: 8px; border: 1px solid #444;">Procesos, memoria y hardware (ej: top, htop, df, ps).</td>
  </tr>
  <tr>
    <td style="background-color: #e65100; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Archivos / Compresión</td>
    <td style="padding: 8px; border: 1px solid #444;">Crear, comprimir y mover (ej: cp, mkdir, 7z, tar).</td>
  </tr>
  <tr>
    <td style="background-color: #00897b; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Transferencia / Web</td>
    <td style="padding: 8px; border: 1px solid #444;">Descargas y envíos remotos (ej: curl, wget, scp, rsync).</td>
  </tr>
  <tr>
    <td style="background-color: #006064; width: 50px; border: 1px solid #444;"></td>
    <td style="padding: 8px; border: 1px solid #444; font-weight: bold;">Paquetes / Updates</td>
    <td style="padding: 8px; border: 1px solid #444;">Instalación de software (ej: apt, dpkg, pacman).</td>
  </tr>
</table>


<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #003366, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD ls</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">List Directory Contents</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td><td style="padding: 10px 15px;">Muestra todos los archivos, incluyendo los ocultos (.).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -a</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-A</td><td style="padding: 10px 15px;">Muestra ocultos, pero excluye los directorios . y ..</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -A</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td><td style="padding: 10px 15px;">Muestra caracteres no gráficos con escapes de estilo C.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -b</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-B</td><td style="padding: 10px 15px;">Ignora archivos que terminan en ~ (copias de seguridad).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -B</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td><td style="padding: 10px 15px;">Ordena por tiempo de cambio de estado (ctime).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -lc</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-C</td><td style="padding: 10px 15px;">Lista las entradas en columnas (vista estándar).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -C</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td><td style="padding: 10px 15px;">Lista directorios como archivos (no su contenido).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -d */</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td><td style="padding: 10px 15px;">No ordena el listado; activa -aU.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -f</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-F</td><td style="padding: 10px 15px;">Clasifica con símbolos (/, *, @, |, =).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -F</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-g</td><td style="padding: 10px 15px;">Como -l, pero omite la columna del propietario.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -g</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-G</td><td style="padding: 10px 15px;">En listado largo, omite la columna del grupo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -lG</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-h</td><td style="padding: 10px 15px;">Tamaños legibles para humanos (KB, MB, GB).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -lh</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td><td style="padding: 10px 15px;">Muestra el número de nodo índice (inode).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -i</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-l</td><td style="padding: 10px 15px;">Usa el formato de listado largo y detallado.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -l</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td><td style="padding: 10px 15px;">Sigue enlaces simbólicos y muestra el destino.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -L</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-m</td><td style="padding: 10px 15px;">Rellena el ancho con nombres separados por comas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -m</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td><td style="padding: 10px 15px;">Como -l, pero con UID y GID numéricos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -n</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-o</td><td style="padding: 10px 15px;">Como -l, pero omite información de grupo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -o</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-p</td><td style="padding: 10px 15px;">Añade una barra / a cada directorio.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -p</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-q</td><td style="padding: 10px 15px;">Sustituye caracteres no gráficos por signos ?.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -q</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r</td><td style="padding: 10px 15px;">Invierte el orden del listado.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -r</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-R</td><td style="padding: 10px 15px;">Lista subdirectorios de forma recursiva.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -R</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td><td style="padding: 10px 15px;">Muestra el tamaño de cada archivo en bloques.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -s</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-S</td><td style="padding: 10px 15px;">Ordena por tamaño de archivo (mayor primero).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -S</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-t</td><td style="padding: 10px 15px;">Ordena por fecha de modificación (más reciente primero).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -t</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-u</td><td style="padding: 10px 15px;">Ordena por último acceso (atime).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -lu</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-U</td><td style="padding: 10px 15px;">No ordena; según el orden del sistema de archivos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -U</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td><td style="padding: 10px 15px;">Ordenación natural de versiones en el texto.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -v</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-w</td><td style="padding: 10px 15px;">Ajusta el ancho de pantalla manual (ej. -w 80).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -w 80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-x</td><td style="padding: 10px 15px;">Lista las entradas por filas en vez de columnas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -x</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-X</td><td style="padding: 10px 15px;">Ordena alfabéticamente por la extensión.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -X</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-1</td><td style="padding: 10px 15px;">Lista un solo archivo por línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ls -1</code></td></tr>
    </tbody>
  </table>
</div>


<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #cc0000, #1a1a1a); border-bottom: 2px solid #ff4d4d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff4d4d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">💀 CMD rm</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Eliminar archivos o directorios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Modo forzado. Ignora archivos inexistentes y no pide confirmación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -f file.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Modo interactivo. Pide confirmación antes de cada eliminación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -i *.jpg</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-I</td>
        <td style="padding: 10px 15px;">Pregunta una vez antes de borrar más de tres archivos o en borrado recursivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -I *</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Elimina directorios y sus contenidos de forma recursiva.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -r folder/</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Elimina directorios vacíos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -d empty_dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verbose. Explica qué se está borrando en cada momento.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -v file.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">--one-file-system</td>
        <td style="padding: 10px 15px;">Al borrar recursivamente, ignora directorios que estén en otros sistemas de archivos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -r --one-file-system /</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">--no-preserve-root</td>
        <td style="padding: 10px 15px;">No trata la raíz '/' de forma especial (permite borrar todo el sistema).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -rf --no-preserve-root /</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">--preserve-root</td>
        <td style="padding: 10px 15px;">Falla si se intenta realizar una operación recursiva en la raíz '/' (activado por defecto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rm -rf --preserve-root /</code></td>
      </tr>
    </tbody>
  </table>
</div>


<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD diff</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Compara archivos línea por línea</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Modo breve. Solo indica si los archivos difieren, no muestra los cambios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -q a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Informa explícitamente cuando dos archivos son idénticos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -s a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Formato de contexto. Muestra algunas líneas antes y después del cambio.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -c a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Formato unificado. Es el más común para crear parches (patches).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -u a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-y</td>
        <td style="padding: 10px 15px;">Muestra la salida en dos columnas (lado a lado).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -y a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Ignora todos los espacios en blanco al comparar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -w a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Ignora mayúsculas y minúsculas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -i a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Compara directorios de forma recursiva.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -r dir1/ dir2/</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-B</td>
        <td style="padding: 10px 15px;">Ignora cambios que solo implican líneas en blanco.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff -B a.txt b.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--brief</td>
        <td style="padding: 10px 15px;">Equivalente a -q; solo indica si hay diferencias.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">diff --brief a.txt b.txt</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1e5d1e, #1a1a1a); border-bottom: 2px solid #2d8a2d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4dfa4d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🌐 CMD GOBUSTER</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Herramienta de fuerza bruta para URIs, DNS y VHosts</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">dir</td>
        <td style="padding: 10px 15px;">Modo clásico para enumerar directorios y archivos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gobuster dir -u ...</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">dns</td>
        <td style="padding: 10px 15px;">Modo de enumeración de subdominios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gobuster dns -d ...</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-u, --url</td>
        <td style="padding: 10px 15px;">URL objetivo (debe incluir http:// o https://).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-u http://site.com</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-w, --wordlist</td>
        <td style="padding: 10px 15px;">Ruta al diccionario que se va a utilizar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-w /usr/share/seclists/...</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-x, --extensions</td>
        <td style="padding: 10px 15px;">Extensiones de archivo a buscar (php, html, txt).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-x php,txt,js</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-t, --threads</td>
        <td style="padding: 10px 15px;">Número de hilos concurrentes (por defecto 10).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-t 50</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-k, --no-tls-validation</td>
        <td style="padding: 10px 15px;">Ignora errores de certificados SSL/TLS.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-k</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-o, --output</td>
        <td style="padding: 10px 15px;">Guarda el resultado en un archivo de texto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-o scan.txt</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1e5d1e, #1a1a1a); border-bottom: 2px solid #2d8a2d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4dfa4d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">⚡ CMD WFUZZ</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Web Fuzzer avanzado para descubrir vulnerabilidades</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Especifica el diccionario (wordlist) a usar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-w lista.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">FUZZ</td>
        <td style="padding: 10px 15px;">Palabra clave donde se inyectará el diccionario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">u.com/FUZZ</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">--hc / --sc</td>
        <td style="padding: 10px 15px;">Ocultar o mostrar códigos de estado específicos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">--hc 404</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">--hw / --hl</td>
        <td style="padding: 10px 15px;">Ocultar respuestas por número de palabras o líneas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">--hw 12</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Datos para peticiones POST.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-d "id=FUZZ"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-H</td>
        <td style="padding: 10px 15px;">Añade cabeceras personalizadas (Headers).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-H "Host: FUZZ"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Número de conexiones concurrentes.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-t 20</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4dfa4d; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">URL del objetivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">-u http://...</code></td>
      </tr>
    </tbody>
  </table>
</div>


<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🌐 CMD nmap </span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Escaneo de red y auditoría completa</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">DESCUBRIMIENTO DE HOSTS</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sL</td>
        <td style="padding: 10px 15px;">List Scan - Simplemente lista los objetivos a escanear.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sL 192.168.1.*</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sn</td>
        <td style="padding: 10px 15px;">Ping Scan - Desactiva el escaneo de puertos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sn 10.0.0.0/24</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-Pn</td>
        <td style="padding: 10px 15px;">Trata a todos los hosts como online (omite descubrimiento).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -Pn target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-PS</td>
        <td style="padding: 10px 15px;">TCP SYN Ping a puertos específicos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -PS22,80 target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-PA</td>
        <td style="padding: 10px 15px;">TCP ACK Ping a puertos específicos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -PA target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-PU</td>
        <td style="padding: 10px 15px;">UDP Ping a puertos específicos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -PU target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-n / -R</td>
        <td style="padding: 10px 15px;">No realizar resolución DNS / Forzar resolución DNS.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -n target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">TÉCNICAS DE ESCANEO (SCAN)</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sS</td>
        <td style="padding: 10px 15px;">TCP SYN Scan (Sigiloso).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sS target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sT</td>
        <td style="padding: 10px 15px;">TCP Connect Scan (Completa el handshake).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sT target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sU</td>
        <td style="padding: 10px 15px;">Escaneo de puertos UDP.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sU target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sA</td>
        <td style="padding: 10px 15px;">TCP ACK Scan (Para mapear reglas de firewall).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sA target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sN / -sF / -sX</td>
        <td style="padding: 10px 15px;">Null, FIN, y Xmas scans (Escaneos avanzados).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sX target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">ESPECIFICACIÓN DE PUERTOS</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Escanea puertos específicos. Ej: -p22,80 o -p1-65535 o -p-.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -p 80 target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-F</td>
        <td style="padding: 10px 15px;">Fast mode - Escanea menos puertos que el default.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -F target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Escanea puertos secuencialmente (no aleatorio).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -r target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">DETECCIÓN DE VERSIONES Y SO</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sV</td>
        <td style="padding: 10px 15px;">Detección de versiones de servicios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sV target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-O</td>
        <td style="padding: 10px 15px;">Detección de Sistema Operativo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -O target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-A</td>
        <td style="padding: 10px 15px;">Agresivo: -O, -sV, -sC (scripts) y traceroute.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -A target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">RENDIMIENTO Y TIMING</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-T[0-5]</td>
        <td style="padding: 10px 15px;">Plantilla de tiempo (0: paranoico, 5: loco).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -T4 target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">--min-rate</td>
        <td style="padding: 10px 15px;">Envía paquetes no más lento que X por segundo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap --min-rate 1000 target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">EVASIÓN DE FIREWALL / IDS</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Fragmentar paquetes.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -f target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-S</td>
        <td style="padding: 10px 15px;">Suplantar dirección IP de origen (Spoofing).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -S IP_Falsa target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Usar interfaz de red específica.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -e eth0 target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-D</td>
        <td style="padding: 10px 15px;">Escaneo con señuelos (Decoys) para ocultar tu IP.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -D RND:10 target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">FORMATOS DE SALIDA</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-oN</td>
        <td style="padding: 10px 15px;">Salida normal a archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -oN file.txt target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-oX</td>
        <td style="padding: 10px 15px;">Salida en formato XML.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -oX file.xml target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-oG</td>
        <td style="padding: 10px 15px;">Salida "grepable" (fácil de filtrar con grep).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -oG file.grep target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-oA</td>
        <td style="padding: 10px 15px;">Guarda en los 3 formatos principales a la vez.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -oA base_name target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">MOTOR DE SCRIPTS (NSE)</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-sC</td>
        <td style="padding: 10px 15px;">Ejecuta los scripts por defecto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -sC target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">--script</td>
        <td style="padding: 10px 15px;">Ejecuta scripts específicos o categorías (vuln, auth, etc).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap --script vuln target</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e2a1e;">
        <td colspan="3" style="padding: 8px 15px; color: #2eb82e; font-weight: bold; font-size: 0.8em;">OTROS</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-6</td>
        <td style="padding: 10px 15px;">Habilita escaneo IPv6.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -6 target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-v / -vv</td>
        <td style="padding: 10px 15px;">Aumentar nivel de verbosidad (detalles en pantalla).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -vv target</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Muestra la ayuda resumen.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nmap -h</code></td>
      </tr>

      <tr style="border-bottom: 2px solid #2eb82e; background: linear-gradient(to right, #1a5d1a, #1a1a1a);">
        <td colspan="3" style="padding: 12px 15px; color: #2eb82e; font-weight: bold; font-size: 1.1em; letter-spacing: 1px;">SCRIPTS (NSE)</td>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left;">Nombre / Categoría</th>
        <th style="padding: 10px 15px; text-align: left;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left;">Puertos</th>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">auth</td>
        <td style="padding: 10px 15px;">Prueba credenciales por defecto o bypass de autenticación.</td>
        <td style="padding: 10px 15px; color: #aaa;">21, 22, 23, 80, 443, 445</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">brute</td>
        <td style="padding: 10px 15px;">Ataques de fuerza bruta contra protocolos de login.</td>
        <td style="padding: 10px 15px; color: #aaa;">21, 22, 23, 3306, 5432, 1433</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">vuln</td>
        <td style="padding: 10px 15px;">Busca vulnerabilidades específicas conocidas (CVEs).</td>
        <td style="padding: 10px 15px; color: #aaa;">80, 443, 445, 3389</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">discovery</td>
        <td style="padding: 10px 15px;">Enumera información adicional (Nombres, SMB, SNMP).</td>
        <td style="padding: 10px 15px; color: #aaa;">53, 137, 161, 445</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">http-enum</td>
        <td style="padding: 10px 15px;">Enumera directorios y archivos comunes en servidores Web.</td>
        <td style="padding: 10px 15px; color: #aaa;">80, 443, 8080</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">smb-vuln-ms17-010</td>
        <td style="padding: 10px 15px;">Verifica específicamente vulnerabilidad EternalBlue.</td>
        <td style="padding: 10px 15px; color: #aaa;">445</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">ssh-auth-methods</td>
        <td style="padding: 10px 15px;">Lista los métodos de autenticación aceptados por SSH.</td>
        <td style="padding: 10px 15px; color: #aaa;">22</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">ftp-anon</td>
        <td style="padding: 10px 15px;">Comprueba si el servidor FTP permite acceso anónimo.</td>
        <td style="padding: 10px 15px; color: #aaa;">21</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">rdp-vuln-ms12-020</td>
        <td style="padding: 10px 15px;">Busca vulnerabilidades críticas en el servicio de RDP.</td>
        <td style="padding: 10px 15px; color: #aaa;">3389</td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">mysql-info</td>
        <td style="padding: 10px 15px;">Extrae versión e información de configuración de MySQL.</td>
        <td style="padding: 10px 15px; color: #aaa;">3306</td>
      </tr>
    </tbody>
  </table>
</div>




<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD grep</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Búsqueda de patrones en archivos o salida</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Especifica un patrón. Útil para patrones que empiezan por "-".</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -e "patron"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Obtiene los patrones de un archivo, uno por línea.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -f lista.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Ignora mayúsculas y minúsculas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -i "error"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Invierte la selección: muestra las líneas que NO coinciden.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -v "info"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Busca la palabra completa únicamente.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -w "fin"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-x</td>
        <td style="padding: 10px 15px;">Busca coincidencias que ocupen la línea completa.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -x "linea"</code></td>
      </tr>
      
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Muestra solo el conteo de líneas que coinciden.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -c "bash"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Muestra solo el nombre de los archivos que NO coinciden.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -L "test" *</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Muestra solo el nombre de los archivos que coinciden.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -l "conf"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Detiene la lectura tras un número determinado de coincidencias.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -m 5 "log"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-o</td>
        <td style="padding: 10px 15px;">Muestra solo la parte de la línea que coincide (no la línea entera).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -o "[0-9]*"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Modo silencioso. No escribe nada en la salida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -q "check"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Suprime mensajes de error sobre archivos inexistentes o ilegibles.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -s "root" /etc/</code></td>
      </tr>
      
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Muestra el desplazamiento en bytes antes de cada línea.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -b "id"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-H</td>
        <td style="padding: 10px 15px;">Muestra el nombre del archivo para cada coincidencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -H "pass"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">No muestra el nombre del archivo en la salida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -h "txt"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Muestra el número de línea de cada coincidencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -n "TODO"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-T</td>
        <td style="padding: 10px 15px;">Tabula la salida para que los números de línea se alineen.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -nT "fix"</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-A</td>
        <td style="padding: 10px 15px;">Muestra N líneas después (After) de la coincidencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -A 3 "user"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-B</td>
        <td style="padding: 10px 15px;">Muestra N líneas antes (Before) de la coincidencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -B 2 "start"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-C</td>
        <td style="padding: 10px 15px;">Muestra N líneas de contexto antes y después.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -C 5 "key"</code></td>
      </tr>

      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Búsqueda recursiva en directorios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -r "pattern" /var/log/</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-E</td>
        <td style="padding: 10px 15px;">Interpreta el patrón como una expresión regular extendida (ERE).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -E "a|b"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-F</td>
        <td style="padding: 10px 15px;">Interpreta el patrón como una cadena fija (Fixed string).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -F ".*"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">Interpreta el patrón como una expresión regular de Perl (PCRE).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -P "\d{3}"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-I</td>
        <td style="padding: 10px 15px;">Ignora archivos binarios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -I "text" *</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-V</td>
        <td style="padding: 10px 15px;">Muestra información de la versión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep -V</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🖼️ CMD feh</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Visor de imágenes ligero</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-A</td><td style="padding: 10px 15px;">Ejecuta una acción personalizada al presionar una tecla.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -A "mv %f ~/bak"</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-B</td><td style="padding: 10px 15px;">Establece el color de fondo para imágenes transparentes.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -B white img.png</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td><td style="padding: 10px 15px;">Dibuja el nombre del archivo sobre la imagen.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -d img.jpg</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-F</td><td style="padding: 10px 15px;">Modo pantalla completa.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -F img.jpg</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-g</td><td style="padding: 10px 15px;">Define la geometría (ancho x alto) de la ventana.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -g 800x600</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-l</td><td style="padding: 10px 15px;">Lista los archivos de imagen en formato de tabla.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -l</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-m</td><td style="padding: 10px 15px;">Modo montaje: crea una miniatura de todas las imágenes.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -m ./pics</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r</td><td style="padding: 10px 15px;">Busca imágenes de forma recursiva en directorios.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -r ./</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-z</td><td style="padding: 10px 15px;">Aleatoriza el orden de las imágenes (Randomize).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -z ./pics</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-D</td><td style="padding: 10px 15px;">Modo diapositivas con retraso de N segundos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -D 2 *.png</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--bg-fill</td><td style="padding: 10px 15px;">Establece el fondo de pantalla rellenando (ajustado).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh --bg-fill img.jpg</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-V</td><td style="padding: 10px 15px;">Muestra la versión de feh.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">feh -V</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🐱 CMD cat</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Concatenar y mostrar archivos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-A</td><td style="padding: 10px 15px;">Equivalente a -vET (muestra todo incluyendo caracteres no imprimibles).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -A file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td><td style="padding: 10px 15px;">Enumera líneas que no están vacías.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -b file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-e</td><td style="padding: 10px 15px;">Equivalente a -vE.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -e file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-E</td><td style="padding: 10px 15px;">Muestra un "$" al final de cada línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -E file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td><td style="padding: 10px 15px;">Enumera todas las líneas de salida (incluyendo vacías).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -n file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td><td style="padding: 10px 15px;">Suprime líneas vacías consecutivas (las une en una sola).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -s file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-t</td><td style="padding: 10px 15px;">Equivalente a -vT.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -t file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-T</td><td style="padding: 10px 15px;">Muestra los caracteres de tabulación como ^I.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -T file.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td><td style="padding: 10px 15px;">Muestra caracteres no imprimibles (excepto saltos y tabs).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">cat -v file.txt</code></td></tr>
    </tbody>
  </table>
</div>


<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #cc0000, #1a1a1a); border-bottom: 2px solid #ff4d4d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff4d4d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔒 CMD chattr</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Cambiar atributos de archivos en Linux</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-R</td><td style="padding: 10px 15px;">Cambia atributos de directorios y su contenido recursivamente.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr -R +i dir/</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-v</td><td style="padding: 10px 15px;">Establece el número de versión/generación del archivo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr -v 2 file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">-f</td><td style="padding: 10px 15px;">Suprime la mayoría de los mensajes de error.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr -f +i file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #1e1e1e;"><td colspan="3" style="padding: 8px 15px; color: #ff4d4d; font-size: 0.8em; font-weight: bold;">ATRIBUTOS COMUNES (Usar con + , - o =)</td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">i</td><td style="padding: 10px 15px;">Inmutable: El archivo no se puede borrar, renombrar ni modificar.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr +i file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">a</td><td style="padding: 10px 15px;">Append only: Solo permite añadir datos al final del archivo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr +a log.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">S</td><td style="padding: 10px 15px;">Sincronizado: Los cambios se escriben físicamente al disco al instante.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr +S file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">s</td><td style="padding: 10px 15px;">Borrado seguro: Al borrar, los bloques se llenan con ceros.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr +s secret</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">u</td><td style="padding: 10px 15px;">No borrable: Si se borra, sus datos se guardan para recuperación.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr +u file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff4d4d; font-weight: bold;">c</td><td style="padding: 10px 15px;">Comprimido: El núcleo comprime el archivo en disco automáticamente.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">chattr +c file</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">👥 CMD chgrp</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Cambiar la pertenencia de grupo de archivos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Informa solo cuando se realiza un cambio real.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -c admin file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Suprime la mayoría de los mensajes de error.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -f staff file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Muestra un diagnóstico para cada archivo procesado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -v dev log.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Opera en archivos y directorios de forma recursiva.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -R web /var/www</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Afecta a los enlaces simbólicos en lugar de a los archivos referenciados.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -h root link</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-H</td>
        <td style="padding: 10px 15px;">Si el argumento es un enlace simbólico a un directorio, lo recorre.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -RH staff link_dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Recorre todos los enlaces simbólicos a directorios encontrados.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -RL dev .</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">No recorre ningún enlace simbólico (comportamiento por defecto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp -RP root /bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--reference</td>
        <td style="padding: 10px 15px;">Usa el grupo de un archivo de referencia en lugar de un valor.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp --reference=f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--dereference</td>
        <td style="padding: 10px 15px;">Afecta al referente de cada enlace simbólico.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chgrp --dereference ...</code></td>
      </tr>
    </tbody>
  </table>
</div>
<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">👤 CMD chown</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Cambiar el propietario y el grupo de archivos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Reporta solo cuando ocurre un cambio.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -c user file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Fuerza la operación, suprimiendo errores.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -f user file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Verboso; describe cada acción realizada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -v u:g file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Recursivo; afecta a subdirectorios y archivos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -R user dir/</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Afecta a los enlaces simbólicos, no al destino.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -h user link</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-H</td>
        <td style="padding: 10px 15px;">Sigue enlaces simbólicos de la línea de comandos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -RH user link</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Sigue todos los enlaces simbólicos mientras recorre.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -RL user dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">No sigue ningún enlace simbólico (por defecto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown -RP user dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--from</td>
        <td style="padding: 10px 15px;">Cambia el dueño solo si coincide con el actual especificado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown --from=root u2 f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--reference</td>
        <td style="padding: 10px 15px;">Copia el dueño/grupo de un archivo base.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown --reference=r f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--dereference</td>
        <td style="padding: 10px 15px;">Afecta al referente de los enlaces simbólicos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chown --dereference ...</code></td>
      </tr>
    </tbody>
  </table>
</div>
<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🛡️ CMD getcap</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Examinar las capacidades (capabilities) de archivos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Búsqueda recursiva en el árbol de directorios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">getcap -r /usr/bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Muestra todos los archivos, incluso si no tienen capacidades asignadas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">getcap -v /bin/ls</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Muestra las capacidades utilizando el ID numérico del usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">getcap -n /bin/ping</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--</td>
        <td style="padding: 10px 15px;">Indica el fin de las opciones (útil para archivos que empiezan con guion).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">getcap -- -archivo</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD lsattr</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Listar atributos de archivos en el sistema</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Lista recursivamente los atributos de los directorios y su contenido.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">lsattr -R /etc</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-V</td>
        <td style="padding: 10px 15px;">Muestra la versión del programa lsattr.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">lsattr -V</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Lista todos los archivos de los directorios, incluyendo los que empiezan por punto (.).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">lsattr -a</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Lista directorios como archivos normales en lugar de listar su contenido.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">lsattr -d /home</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Muestra el número de generación del proyecto del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">lsattr -p file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Muestra la versión/número de generación del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">lsattr -v file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Muestra los nombres de los atributos de forma extensa en lugar de abreviada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">lsattr -l file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔨 CMD make</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Automatización de compilación y tareas</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-b / -m</td><td style="padding: 8px 15px;">Ignoradas por compatibilidad con otras versiones de make.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -b</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-B</td><td style="padding: 8px 15px;">Fuerza la reconstrucción de todos los objetivos (Always make).</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -B</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-C</td><td style="padding: 8px 15px;">Cambia al directorio especificado antes de leer el makefile.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -C /dir</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td><td style="padding: 8px 15px;">Imprime información de depuración extremadamente detallada.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -d</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-e</td><td style="padding: 8px 15px;">Las variables de entorno sobrescriben las variables del makefile.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -e</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td><td style="padding: 8px 15px;">Utiliza un archivo específico como makefile.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -f MyFile</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-h</td><td style="padding: 8px 15px;">Imprime el resumen de opciones de ayuda.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -h</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td><td style="padding: 8px 15px;">Ignora todos los errores en las recetas ejecutadas.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -i</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-I</td><td style="padding: 8px 15px;">Especifica un directorio para buscar makefiles incluidos.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -I /include</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-j</td><td style="padding: 8px 15px;">Ejecuta N trabajos simultáneamente (procesamiento paralelo).</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -j4</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-k</td><td style="padding: 8px 15px;">Continúa lo más posible después de un error.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -k</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-l</td><td style="padding: 8px 15px;">No inicia nuevos trabajos si la carga del sistema es mayor que N.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -l 2.5</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-L</td><td style="padding: 8px 15px;">Intenta obtener el tiempo del archivo de los enlaces simbólicos.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -L</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-n</td><td style="padding: 8px 15px;">Modo simulacro: imprime los comandos pero no los ejecuta.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -n</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-o</td><td style="padding: 8px 15px;">No reconstruye el archivo especificado aunque sea antiguo.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -o file.c</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-O</td><td style="padding: 8px 15px;">Agrupa la salida de trabajos paralelos (target, line, recurse).</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -Oline</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-p</td><td style="padding: 8px 15px;">Imprime la base de datos interna (reglas y variables).</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -p</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-q</td><td style="padding: 10px 15px;">Modo consulta: devuelve 0 si el objetivo está al día, si no, distinto de cero.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -q</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-r</td><td style="padding: 8px 15px;">Elimina el uso de las reglas implícitas integradas.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -r</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-R</td><td style="padding: 8px 15px;">Elimina el uso de variables implícitas integradas.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -R</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td><td style="padding: 8px 15px;">Modo silencioso: no imprime las recetas mientras se ejecutan.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -s</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-S</td><td style="padding: 8px 15px;">Cancela el efecto de la opción -k.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -S</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-t</td><td style="padding: 8px 15px;">Toca los archivos (actualiza fecha) en lugar de reconstruirlos.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -t</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-v</td><td style="padding: 8px 15px;">Muestra la versión de make.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -v</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td><td style="padding: 8px 15px;">Imprime el directorio de trabajo antes y después de procesar.</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -w</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-W</td><td style="padding: 8px 15px;">Considera el archivo especificado como "recién modificado".</td><td style="padding: 8px 15px;"><code style="color: #aaa;">make -W file.h</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📁 CMD mkdir</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Crear nuevos directorios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Establece los permisos (modo) del directorio (octal o simbólico).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mkdir -m 755 dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Crea directorios padres si no existen; no da error si ya existe.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mkdir -p a/b/c</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Muestra un mensaje por cada directorio creado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mkdir -v nuevo_dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-Z</td>
        <td style="padding: 10px 15px;">Establece el contexto de seguridad SELinux al valor por defecto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mkdir -Z dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">--context</td>
        <td style="padding: 10px 15px;">Establece un contexto de seguridad SELinux específico.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mkdir --context=CTX</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mkdir --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la información de versión y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mkdir --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📦 CMD mv</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Mover o renombrar archivos y directorios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Realiza una copia de seguridad de cada archivo de destino existente.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -b file.txt /dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Fuerza el movimiento, sobrescribiendo archivos sin preguntar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -f origin dest</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Interactivo; pide confirmación antes de sobrescribir.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -i file.txt /tmp</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">No sobrescribe ningún archivo existente (no-clobber).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -n src dest</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Mueve solo si el origen es más reciente que el destino o si falta el destino.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -u log.old log.new</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso; explica lo que se está haciendo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -v folder/ ..</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Mueve todos los argumentos de origen a un directorio de destino.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -t /dir f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-T</td>
        <td style="padding: 10px 15px;">Trata el destino como un archivo normal, no como un directorio.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -T src dest_file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-S</td>
        <td style="padding: 10px 15px;">Anula el sufijo de copia de seguridad habitual.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -S .bak f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-Z</td>
        <td style="padding: 10px 15px;">Establece el contexto SELinux del archivo de destino al valor por defecto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mv -Z file /var/www</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📝 CMD nano</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Editor de texto en terminal</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-B</td>
        <td style="padding: 10px 15px;">Crea copias de seguridad de los archivos antes de editarlos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -B file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-C</td>
        <td style="padding: 10px 15px;">Define el directorio donde se guardarán las copias de seguridad.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -C ~/backups</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-E</td>
        <td style="padding: 10px 15px;">Convierte tabuladores en espacios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -E code.py</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-I</td>
        <td style="padding: 10px 15px;">No lee los archivos de configuración (nanorc).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -I file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">No añade saltos de línea al final de los archivos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -L text.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Habilita el uso del ratón dentro del editor.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -m config</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Modo solo lectura.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -R /etc/passwd</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-S</td>
        <td style="padding: 10px 15px;">Habilita el desplazamiento suave línea a línea.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -S file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Visualización solamente (similar a -R).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -v file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Muestra constantemente la posición del cursor.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -c script.sh</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Desactiva el ajuste automático de líneas largas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">nano -w file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🛡️ CMD setcap</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Establecer capacidades en archivos ejecutables</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Elimina todas las capacidades del archivo especificado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">setcap -r /bin/ping</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Verifica que las capacidades especificadas coinciden con las del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">setcap -v cap_net_raw+ep exec</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Modo silencioso; solo informa de errores fatales.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">setcap -q ...</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Establece el ID de usuario raíz para el cual la capacidad es válida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">setcap -n 1000 ...</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--</td>
        <td style="padding: 10px 15px;">Fin de las opciones (necesario si el nombre del archivo empieza por guion).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">setcap -- -file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD tail</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Mostrar la última parte de archivos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Muestra los últimos N bytes; con '+N' muestra desde el byte N.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -c 50 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Sigue el archivo en tiempo real (añade datos conforme crecen).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -f /var/log/syslog</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-F</td>
        <td style="padding: 10px 15px;">Igual que -f, pero sigue intentando abrir el archivo si se borra o rota.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -F access.log</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Muestra las últimas N líneas (por defecto 10).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -n 20 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Modo silencioso; nunca imprime encabezados con nombres de archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -q f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso; siempre imprime encabezados con nombres de archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -v file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Con -f, duerme N segundos entre comprobaciones.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -f -s 2 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--pid</td>
        <td style="padding: 10px 15px;">Con -f, termina cuando el proceso con ese PID muere.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail -f file --pid=1234</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--retry</td>
        <td style="padding: 10px 15px;">Sigue intentando abrir el archivo aunque sea inaccesible al inicio.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tail --retry -f log</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔑 CMD chmod</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Cambiar permisos de archivos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Informa solo cuando se realiza un cambio real.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chmod -c 755 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Fuerza la ejecución; suprime la mayoría de mensajes de error.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chmod -f 644 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Muestra un diagnóstico para cada archivo procesado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chmod -v +x script</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Recursivo; aplica cambios a directorios y sus contenidos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chmod -R 777 /dir</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--reference</td>
        <td style="padding: 10px 15px;">Copia los permisos de un archivo de referencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chmod --reference=f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chmod --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión del programa.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">chmod --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📣 CMD echo</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Imprimir texto en pantalla</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">No imprime el salto de línea al final.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">echo -n "Hola"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Habilita la interpretación de escapes de barra invertida (como \n, \t).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">echo -e "L1\nL2"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-E</td>
        <td style="padding: 10px 15px;">Deshabilita la interpretación de escapes de barra invertida (por defecto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">echo -E "L1\nL2"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">echo --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión del comando.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">echo --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📄 CMD touch</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Cambiar marcas de tiempo o crear archivos vacíos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Cambia únicamente la hora de acceso.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -a file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">No crea el archivo si no existe (no-create).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -c file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Usa una cadena de texto para especificar la fecha/hora.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -d "2026-02-09"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Ignorada (para compatibilidad con versiones antiguas de BSD).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -f file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Afecta al enlace simbólico en lugar del archivo referenciado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -h link</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Cambia únicamente la hora de modificación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -m file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Usa las marcas de tiempo de un archivo de referencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -r ref_file f1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Usa el formato [[CC]YY]MMDDhhmm[.ss] en lugar de la hora actual.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch -t 202602091300 f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la información de versión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">touch --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">👯 CMD cp</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Copiar archivos y directorios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Archivo. Preserva todo (permisos, dueños, enlaces, recursividad).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -a dir/ backup/</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Realiza una copia de seguridad antes de sobrescribir.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -b f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Copia enlaces simbólicos como tales, no los archivos que apuntan.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -d link link_bk</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Fuerza la copia; si no puede abrirse el destino, lo borra e intenta de nuevo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -f f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Interactivo. Pide confirmación antes de sobrescribir.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -i f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Crea enlaces duros (hard links) en lugar de copiar archivos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -l f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Sigue siempre los enlaces simbólicos en el origen.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -L link f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">No sobrescribe un archivo existente (no-clobber).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -n f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Preserva permisos, dueños y marcas de tiempo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -p f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">No sigue nunca los enlaces simbólicos en el origen (por defecto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -P link f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Copia directorios de forma recursiva.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -r dir1 dir2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Crea enlaces simbólicos en lugar de copiar archivos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -s f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Copia solo si el origen es más reciente o si el destino no existe.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -u f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso; explica lo que se está haciendo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -v f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-x</td>
        <td style="padding: 10px 15px;">Se queda en este sistema de archivos (no cruza puntos de montaje).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cp -ax / /mnt</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📍 CMD pwd</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Imprimir el directorio de trabajo actual</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Usa la ruta lógica del entorno, incluso si contiene enlaces simbólicos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">pwd -L</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">Evita todos los enlaces simbólicos (muestra la ruta física real).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">pwd -P</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">pwd --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la información de versión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">pwd --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">⚡ CMD sudo</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Ejecutar comandos como superusuario o otro usuario</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Ejecuta el comando como un usuario diferente al root.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -u www-data ls</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-g</td>
        <td style="padding: 10px 15px;">Ejecuta el comando con el grupo primario especificado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -g dev touch f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Lista los privilegios permitidos para el usuario actual.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -l</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Actualiza el "timestamp" del usuario (extiende el tiempo sin pedir pass).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -v</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-k</td>
        <td style="padding: 10px 15px;">Invalida el "timestamp" del usuario (pide password la próxima vez).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -k</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Ejecuta el comando en segundo plano (background).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -b apt update</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-E</td>
        <td style="padding: 10px 15px;">Preserva las variables de entorno del usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -E script.sh</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-H</td>
        <td style="padding: 10px 15px;">Establece la variable HOME al directorio del usuario de destino.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -H bash</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-S</td>
        <td style="padding: 10px 15px;">Lee la contraseña de la entrada estándar (stdin) en lugar de la terminal.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">echo pass | sudo -S ls</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Inicia una shell de login como el usuario de destino.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -i</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Ejecuta la shell especificada en SHELL o la shell por defecto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -s</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Modo no interactivo; falla si requiere que el usuario ingrese pass.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -n apt upgrade</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Usa un prompt de contraseña personalizado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sudo -p "Pass: " ls</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🌳 CMD tree</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Visualización jerárquica de directorios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Muestra todos los archivos, incluidos los ocultos (que empiezan por punto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -a</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Lista únicamente los directorios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -d</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Muestra la ruta completa (prefijo del path) para cada archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">No imprime las líneas de indentación (útil con -f).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -fi</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Nivel máximo de profundidad del árbol.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -L 2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">Lista solo archivos que coincidan con el patrón indicado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -P "*.sh"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-I</td>
        <td style="padding: 10px 15px;">Excluye archivos que coincidan con el patrón indicado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -I "node_modules"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Muestra los permisos (estilo ls -l) para cada archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -p</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-u / -g</td>
        <td style="padding: 10px 15px;">Muestra el nombre del usuario / nombre del grupo dueño del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -ug</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Muestra el tamaño en bytes de cada archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -s</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Muestra el tamaño en formato legible (KB, MB, etc.).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -h</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-D</td>
        <td style="padding: 10px 15px;">Muestra la fecha de la última modificación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -D</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-C</td>
        <td style="padding: 10px 15px;">Activa el uso de colores (útil si no es el default).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -C</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-N</td>
        <td style="padding: 10px 15px;">Muestra caracteres no imprimibles tal cual (no escapados).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tree -N</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">➕ CMD groupadd</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Añadir un nuevo grupo de usuarios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-g</td>
        <td style="padding: 10px 15px;">Define manualmente el GID (ID numérico del grupo).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">groupadd -g 1500 devs</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Fuerza la creación; termina con éxito si el grupo ya existe.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">groupadd -f admin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-o</td>
        <td style="padding: 10px 15px;">Permite crear un grupo con un GID duplicado (con -g).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">groupadd -o -g 0 root2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Establece una contraseña encriptada para el grupo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">groupadd -p "hash" grp</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Crea un grupo de sistema (GID bajo).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">groupadd -r sysusers</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-K</td>
        <td style="padding: 10px 15px;">Sobrescribe valores de /etc/login.defs (ej. GID_MIN).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">groupadd -K GID_MIN=100</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Aplica los cambios en el directorio CHROOT especificado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">groupadd -R /mnt/iso grp</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #6a0dad, #1a1a1a); border-bottom: 2px solid #9d4edd;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #9d4edd; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">👤 CMD usermod</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Modificar cuentas de usuario</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Añade el usuario a los grupos suplementarios (usar solo con -G).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -aG sudo user</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Cambia el campo de comentario (nombre completo) del usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -c "Juan Perez" u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Define un nuevo directorio HOME para el usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -d /home/nuevo u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Fecha en la que la cuenta será desactivada (AAAA-MM-DD).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -e 2026-12-31 u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Días tras expirar la pass para desactivar la cuenta permanentemente.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -f 30 u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-g</td>
        <td style="padding: 10px 15px;">Cambia el grupo primario (nombre o GID) del usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -g developers u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-G</td>
        <td style="padding: 10px 15px;">Define una nueva lista de grupos suplementarios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -G ftp,www u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Cambia el nombre de inicio de sesión (login name) del usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -l nuevo_nick u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Bloquea la contraseña del usuario (pone un '!' al inicio del hash).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -L u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Mueve el contenido del HOME actual al nuevo (usar con -d).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -m -d /new u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-o</td>
        <td style="padding: 10px 15px;">Permite duplicar el UID (usar con -u).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -o -u 0 u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Establece una contraseña encriptada (no recomendada).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -p "hash" u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Define una nueva shell de inicio de sesión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -s /bin/zsh u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Cambia el ID numérico del usuario (UID).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -u 1500 u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-U</td>
        <td style="padding: 10px 15px;">Desbloquea la contraseña del usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -U u1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #9d4edd; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Aplica los cambios en el directorio CHROOT indicado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">usermod -R /mnt u1</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD which</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Localizar la ruta de un comando ejecutable</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Muestra todas las rutas coincidentes en el PATH, no solo la primera.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">which -a python</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra un resumen de ayuda.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">which --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión del programa.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">which --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📦 CMD 7z</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Compresión y descompresión 7-Zip</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Comando/Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #2d1a0a;">
        <td colspan="3" style="padding: 8px 15px; color: #ff944d; font-weight: bold; font-size: 0.8em;">COMANDOS (Sin guion)</td>
      </tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">a</td><td>Añadir archivos al archivo comprimido.</td><td><code style="color: #aaa;">7z a arc.7z file</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">d</td><td>Borrar archivos del archivo comprimido.</td><td><code style="color: #aaa;">7z d arc.7z file</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">e</td><td>Extraer archivos (ignora rutas de directorios).</td><td><code style="color: #aaa;">7z e arc.7z</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">l</td><td>Listar contenido del archivo.</td><td><code style="color: #aaa;">7z l arc.7z</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">t</td><td>Probar integridad del archivo comprimido.</td><td><code style="color: #aaa;">7z t arc.7z</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">u</td><td>Actualizar archivos existentes en el archivo comprimido.</td><td><code style="color: #aaa;">7z u arc.7z</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">x</td><td>Extraer con rutas completas (eXtract).</td><td><code style="color: #aaa;">7z x arc.7z</code></td></tr>
      
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #2d1a0a;">
        <td colspan="3" style="padding: 8px 15px; color: #ff944d; font-weight: bold; font-size: 0.8em;">INTERRUPTORES (Con guion)</td>
      </tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-m</td><td>Define el método de compresión (ej: -mx9 para máximo).</td><td><code style="color: #aaa;">7z a -mx9 arc.7z</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-p</td><td>Establece una contraseña.</td><td><code style="color: #aaa;">7z a -pSECRET arc.7z</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-o</td><td>Define el directorio de salida para la extracción.</td><td><code style="color: #aaa;">7z x arc -o/tmp</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-r</td><td>Recorre directorios de forma recursiva.</td><td><code style="color: #aaa;">7z a -r arc.7z *.txt</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-t</td><td>Especifica el tipo de archivo (7z, zip, tar, etc).</td><td><code style="color: #aaa;">7z a -tzip arc.zip</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-v</td><td>Crea volúmenes (partes) de tamaño específico.</td><td><code style="color: #aaa;">7z a -v100m arc.7z</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-w</td><td>Define el directorio para archivos temporales.</td><td><code style="color: #aaa;">7z a -w/tmp arc.7z</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-y</td><td>Asume "Sí" a todas las preguntas (modo desatendido).</td><td><code style="color: #aaa;">7z x arc.7z -y</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-sdel</td><td>Borra los archivos de origen después de comprimirlos.</td><td><code style="color: #aaa;">7z a arc.7z f -sdel</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-sfx</td><td>Crea un archivo autoextraíble.</td><td><code style="color: #aaa;">7z a -sfx arc.exe</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-i</td><td>Incluye archivos específicos mediante patrones.</td><td><code style="color: #aaa;">7z a arc -ir!*.doc</code></td></tr>
      <tr><td style="padding: 8px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-x</td><td>Excluye archivos específicos mediante patrones.</td><td><code style="color: #aaa;">7z a arc -xr!*.log</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD find</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Búsqueda profunda de archivos en el sistema</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Opción / Prueba</th>
        <th style="padding: 10px 15px; text-align: left; width: 50%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-name</td><td>Busca archivos por nombre (sensible a mayúsculas).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -name "*.txt"</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-iname</td><td>Busca archivos por nombre (ignora mayúsculas).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -iname "README"</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-type</td><td>Filtra por tipo: f (archivo), d (directorio), l (enlace), b/c (dispositivos).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find /dev -type b</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-size</td><td>Busca por tamaño: c (bytes), k (KB), M (MB), G (GB). + o - para rangos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -size +100M</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-mtime</td><td>Archivos modificados hace N días (+N: hace más, -N: hace menos).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -mtime -7</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-atime / -ctime</td><td>Tiempo de acceso / Tiempo de cambio de estado de archivo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -atime +30</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-perm</td><td>Busca archivos con permisos específicos (modo octal o simbólico).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -perm 777</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-user / -group</td><td>Busca archivos pertenecientes a un usuario o grupo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find /home -user root</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-maxdepth</td><td>Nivel máximo de profundidad para descender en los directorios.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -maxdepth 1</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-empty</td><td>Busca archivos o directorios vacíos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -type d -empty</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-exec</td><td>Ejecuta un comando sobre los resultados. Termina con " \;"</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -exec rm {} \;</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-delete</td><td>Borra directamente los archivos encontrados (CUIDADO).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find /tmp -mtime +1 -delete</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-ls</td><td>Muestra los resultados con el formato de "ls -dils".</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find . -ls</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L / -P</td><td>Sigue enlaces simbólicos / No sigue enlaces (por defecto).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">find -L . -name "f"</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📦 CMD tar</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Archivador de ficheros (Tape Archiver)</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-c</td><td>Crea un nuevo archivo (Create).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -cf arc.tar .</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-x</td><td>Extrae el contenido de un archivo (eXtract).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -xf arc.tar</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-t</td><td>Lista el contenido de un archivo (Table).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -tf arc.tar</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-f</td><td>Utiliza el archivo especificado (File). Debe ser la última opción.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -f arc.tar</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-v</td><td>Modo verboso. Muestra el progreso de los archivos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -cvf arc.tar .</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-z</td><td>Comprime/descomprime usando gzip (.tar.gz).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -czf arc.tgz .</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-j</td><td>Comprime/descomprime usando bzip2 (.tar.bz2).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -cjf arc.tbz2 .</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-J</td><td>Comprime/descomprime usando xz (.tar.xz).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -cJf arc.tar.xz .</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-u</td><td>Actualiza archivos que son más recientes que la copia en el archivador.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -uf arc.tar file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-r</td><td>Añade archivos al final de un archivador existente.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -rf arc.tar new</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-A</td><td>Concatena archivos tar a un archivador.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar -Af a1.tar a2.tar</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">--delete</td><td>Borra archivos del archivador (no funciona en cintas).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar --delete -f a.tar f</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">--exclude</td><td>Excluye archivos que coincidan con el patrón.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">tar --exclude="*.log"</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📡 CMD ping</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Enviar paquetes ICMP ECHO_REQUEST a hosts de red</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-c</td><td>Detenerse tras enviar N paquetes.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -c 4 8.8.8.8</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-i</td><td>Intervalo en segundos entre cada paquete (N.N segundos).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -i 0.5 target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-s</td><td>Especifica el número de bytes de datos a enviar.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -s 1000 target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-t</td><td>Establece el TTL (Time To Live) de los paquetes.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -t 64 target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-W</td><td>Tiempo de espera para una respuesta en segundos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -W 1 target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-f</td><td>Flood ping. Envía paquetes tan rápido como puede (solo root).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sudo ping -f target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-a</td><td>Audible ping. Emite un sonido cuando recibe respuesta.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -a target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-n</td><td>Solo salida numérica. No intenta resolver nombres de host.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -n 8.8.8.8</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-v</td><td>Salida detallada (Verbose).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -v target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-I</td><td>Usa la interfaz o dirección IP de origen especificada.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -I eth0 target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-4 / -6</td><td>Fuerza el uso de IPv4 o IPv6 únicamente.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -6 target</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-R</td><td>Registra la ruta (Record route). Muestra los saltos realizados.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ping -R target</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔄 CMD rev</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Invertir líneas de caracteres</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-V</td>
        <td style="padding: 10px 15px;">Muestra información de la versión y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rev -V</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Muestra la ayuda de uso y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rev -h</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--</td>
        <td style="padding: 10px 15px;">Indica el fin de las opciones (útil para nombres de archivos que empiezan por guion).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">rev -- -archivo</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔝 CMD head</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Mostrar las primeras líneas de un archivo</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Imprime los primeros N bytes de cada archivo. Con '-', imprime todo excepto los últimos N bytes.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">head -c 100 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Imprime las primeras N líneas (por defecto 10). Con '-', imprime todo excepto las últimas N líneas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">head -n 5 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Modo silencioso; nunca imprime encabezados con nombres de archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">head -q f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso; siempre imprime encabezados con nombres de archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">head -v file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-z</td>
        <td style="padding: 10px 15px;">Delimitador de línea es NUL, no nueva línea.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">head -z file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">head --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">head --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔢 CMD seq</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Imprimir una secuencia de números</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Usa un formato de estilo printf de coma flotante.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">seq -f "N%02g" 5</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Usa la cadena especificada para separar los números (por defecto \n).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">seq -s ", " 3</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Iguala el ancho de los números rellenando con ceros a la izquierda.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">seq -w 1 10</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">seq --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">seq --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📑 CMD sort</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Ordenar líneas de archivos de texto</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-b</td><td>Ignora los espacios en blanco iniciales.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -b file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td><td>Orden de "diccionario": ignora todo lo que no sean letras, números o espacios.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -d file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td><td>Ignora la diferencia entre mayúsculas y minúsculas (fold case).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -f file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-g</td><td>Orden numérico general (soporta notación científica).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -g file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-h</td><td>Ordena números legibles por humanos (ej: 2K, 1G).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -h file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td><td>Ignora caracteres que no son imprimibles.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -i file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-k</td><td>Ordena por una clave (columna) específica.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -k 2 file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-m</td><td>Combina archivos ya ordenados (merge).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -m f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-n</td><td>Orden numérico de cadenas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -n file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-o</td><td>Escribe el resultado en un archivo en lugar de la salida estándar.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -o out file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-r</td><td>Invierte el resultado de la comparación (Reverse).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -r file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-R</td><td>Orden aleatorio (Random) basado en hashes.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -R file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td><td>Orden estable (mantiene el orden original de líneas iguales).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -s file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-t</td><td>Define un separador de campos diferente al espacio/tab.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -t: -k3 file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-u</td><td>Único: elimina líneas duplicadas en el resultado.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -u file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-V</td><td>Ordena según números de versión de forma natural.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sort -V file</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🚫 CMD uniq</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Filtrar líneas repetidas consecutivas</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-c</td><td>Muestra el número de veces que se repite una línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -c file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td><td>Muestra únicamente las líneas que están duplicadas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -d file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-D</td><td>Imprime todas las líneas duplicadas (todas las ocurrencias).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -D file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td><td>Evita comparar los primeros N campos de cada línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -f 2 file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td><td>Ignora mayúsculas y minúsculas al comparar.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -i file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td><td>Evita comparar los primeros N caracteres de cada línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -s 5 file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-u</td><td>Muestra únicamente las líneas que no están repetidas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -u file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td><td>Compara como máximo N caracteres de cada línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -w 10 file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-z</td><td>Delimita las líneas con NUL en lugar de nueva línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">uniq -z file</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">💎 CMD strings</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Extraer texto legible de archivos binarios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-a</td><td>Escanea todo el archivo, no solo las secciones de datos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -a binary</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td><td>Muestra solo las cadenas de las secciones de datos cargadas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -d binary</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td><td>Imprime el nombre del archivo antes de cada cadena.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -f *</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-n</td><td>Establece la longitud mínima de la cadena (por defecto 4).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -n 8 bin</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-o</td><td>Equivalente a -t o (offset en octal).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -o binary</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-t</td><td>Imprime el offset de la cadena en formato: d (decimal), o (octal), x (hex).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -t x bin</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-e</td><td>Define la codificación: s (7-bit), S (8-bit), l (16-bit little), b (16-bit big).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -e l bin</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-T</td><td>Especifica el formato del archivo binario (target).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">strings -T elf32...</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📄 CMD file</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Determinar el tipo de archivo</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td><td>Modo breve. No muestra el nombre del archivo en la salida.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -b image.png</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td><td>Muestra la forma analizada del archivo magic (depuración).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -c</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-E</td><td>En errores del sistema (archivo no encontrado), sale con error en lugar de mostrarlo como tipo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -E f.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td><td>Lee los nombres de los archivos a examinar desde un archivo.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -f lista.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-F</td><td>Usa el separador especificado en lugar del ":" predeterminado.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -F " -> " f.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td><td>Muestra el tipo MIME y la codificación de caracteres.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -i script.sh</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-k</td><td>Sigue buscando después de la primera coincidencia (Keep going).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -k binary</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td><td>Sigue enlaces simbólicos (por defecto no los sigue).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -L link_file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-m</td><td>Usa un archivo alternativo de números mágicos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -m mymagic f</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td><td>Fuerza el vaciado de stdout después de cada archivo analizado.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -n f.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-p</td><td>Preserva el tiempo de acceso de los archivos analizados.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -p data.bin</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td><td>Lee archivos de dispositivo o especiales (ej. bloques).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">sudo file -s /dev/sda1</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-z</td><td>Intenta mirar dentro de archivos comprimidos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">file -z backup.tar.gz</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📖 CMD less</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Paginador de texto interactivo</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td><td>Comienza la búsqueda después de la última línea mostrada en pantalla.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -a log.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td><td>Repinta la pantalla de arriba hacia abajo en lugar de desplazarla.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -c file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-e</td><td>Cierra automáticamente al llegar al final del archivo por segunda vez.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -e file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-E</td><td>Cierra automáticamente al llegar al final del archivo la primera vez.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -E file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td><td>Fuerza la apertura de archivos no regulares (directorios o binarios).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -f /dev/sda</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-g</td><td>Resalta solo la coincidencia actual de la búsqueda, no todas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -g file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td><td>Ignora mayúsculas en las búsquedas a menos que el patrón las contenga.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -i file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-M</td><td>Muestra una barra de estado más detallada (líneas, porcentaje).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -M file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-N</td><td>Muestra números de línea al inicio de cada línea.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -N config</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-S</td><td>Corta las líneas largas en lugar de ajustarlas al ancho de pantalla.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -S log.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-x</td><td>Establece el tamaño de los tabuladores (por defecto 8).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -x4 code.c</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-X</td><td>No limpia la pantalla al salir de less.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">less -X file</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔐 CMD base64</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Codificación y decodificación Base64</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td><td>Decodifica los datos de entrada (por defecto codifica).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">base64 -d hash.txt</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td><td>Ignora caracteres no alfabéticos al decodificar.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">base64 -di file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td><td>Ajusta la salida a N caracteres por línea (0 desactiva el ajuste).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">base64 -w 0 file</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td><td>Muestra la ayuda y sale.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">base64 --help</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--version</td><td>Muestra la versión del programa.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">base64 --version</code></td></tr>
    </tbody>
  </table>
</div>
<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔢 CMD hexdump</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Visualización de datos en diversos formatos (hex, octal, etc.)</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Muestra bytes en octal (un byte por cada tres columnas).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -b file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Muestra caracteres en ASCII (un carácter por cada tres columnas).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -c file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-C</td>
        <td style="padding: 10px 15px;">Formato canónico: hexadecimal y ASCII lado a lado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -C binary</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Muestra palabras de dos bytes en decimal sin signo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -d file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Especifica una cadena de formato personalizada para la salida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -e '1/4 "%08x" "\n"'</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Especifica un archivo que contiene las cadenas de formato.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -f fmt.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Interpreta únicamente N bytes de la entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -n 512 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-o</td>
        <td style="padding: 10px 15px;">Muestra palabras de dos bytes en octal.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -o file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Salta N bytes desde el inicio de la entrada (offset).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -s 1024 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso; muestra todas las líneas (no usa "*" para duplicados).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -v file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-x</td>
        <td style="padding: 10px 15px;">Muestra palabras de dos bytes en hexadecimal.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">hexdump -x file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔐 CMD base32</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Codificación y decodificación Base32</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Decodifica los datos de entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">base32 -d encoded.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Ignora caracteres no alfabéticos al decodificar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">base32 -di file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Ajusta la salida a N caracteres por línea (0 desactiva el ajuste).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">base32 -w 76 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">base32 --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión del programa.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">base32 --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔐 CMD base85 (basenc)</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Codificación y decodificación Base85</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--base85</td>
        <td style="padding: 10px 15px;">Selecciona el modo de codificación Base85.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">basenc --base85 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Decodifica los datos de entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">basenc --base85 -d file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Ignora caracteres no alfabéticos al decodificar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">basenc -di --base85 f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Ajusta la salida a N caracteres por línea (0 desactiva el ajuste).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">basenc --base85 -w 0</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--z85</td>
        <td style="padding: 10px 15px;">Usa la variante Z85 (ZeroMQ).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">basenc --z85 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">basenc --help</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #008b8b, #1a1a1a); border-bottom: 2px solid #00cccc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #00cccc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔐 CMD openssl</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Herramientas de criptografía y certificados SSL/TLS</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-help</td>
        <td style="padding: 10px 15px;">Muestra el resumen de uso para el subcomando especificado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl s_client -help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">list</td>
        <td style="padding: 10px 15px;">Lista algoritmos, comandos o funciones disponibles.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl list -cipher-commands</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">enc</td>
        <td style="padding: 10px 15px;">Comando para cifrado/descifrado simétrico.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl enc -aes-256-cbc</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">dgst</td>
        <td style="padding: 10px 15px;">Genera hashes (Message Digests) de archivos o entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl dgst -sha256 f.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-in</td>
        <td style="padding: 10px 15px;">Especifica el archivo de entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl dgst -in file.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-out</td>
        <td style="padding: 10px 15px;">Especifica el archivo de salida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl enc -out out.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-e / -d</td>
        <td style="padding: 10px 15px;">Cifrar / Descifrar (usar con el comando enc).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl aes-256-cbc -d</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Procesa la salida/entrada en formato Base64.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl enc -a -in f.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-pass</td>
        <td style="padding: 10px 15px;">Especifica la fuente de la contraseña (pass:X, file:X, env:X).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">openssl enc -pass pass:123</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔢 CMD od</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Volcado de archivos en diversos formatos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Igual que -t a (nombres de caracteres con nombre).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -a file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Igual que -t o1 (bytes en octal).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -b file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Igual que -t c (caracteres ASCII o secuencias de escape).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -c file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Igual que -t u2 (unidades de 2 bytes en decimal sin signo).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -d file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Igual que -t fF (punto flotante).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -f file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Igual que -t dI (decimal con signo).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -i file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-j</td>
        <td style="padding: 10px 15px;">Salta N bytes desde el inicio de la entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -j 100 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-N</td>
        <td style="padding: 10px 15px;">Muestra únicamente N bytes de la entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -N 50 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-o</td>
        <td style="padding: 10px 15px;">Igual que -t o2 (unidades de 2 bytes en octal).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -o file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Igual que -t d2 (unidades de 2 bytes en decimal).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -s file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Selecciona el formato de salida: a, c, d, f, o, u, x.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -t x1 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Muestra todos los datos (no suprime líneas duplicadas con "*").</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -v file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-x</td>
        <td style="padding: 10px 15px;">Igual que -t x2 (unidades de 2 bytes en hexadecimal).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">od -x file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🗜️ CMD gzip</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Compresión de archivos .gz</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Escribe el resultado en la salida estándar (mantiene el original).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -c f > f.gz</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Descomprime el archivo (equivale a gunzip).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -d file.gz</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Fuerza la compresión o descompresión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -f file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-k</td>
        <td style="padding: 10px 15px;">Mantiene (keep) los archivos de entrada durante la operación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -k file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Lista información sobre el archivo comprimido (ratio, tamaño).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -l file.gz</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">No guarda el nombre original ni el timestamp del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -n file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-N</td>
        <td style="padding: 10px 15px;">Guarda el nombre y timestamp original (por defecto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -N file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Recorre directorios de forma recursiva.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -r folder/</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Comprueba la integridad del archivo comprimido (test).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -t file.gz</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso; muestra el porcentaje de reducción.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -v file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-#</td>
        <td style="padding: 10px 15px;">Nivel de compresión de 1 (rápido) a 9 (mejor).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">gzip -9 file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #4a4a4a, #1a1a1a); border-bottom: 2px solid #888;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #bbb; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🐚 CMD bash</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Bourne-Again SHell, intérprete de comandos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Lee y ejecuta comandos desde el primer argumento no opcional.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash -c "ls /tmp"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Fuerza que la shell sea interactiva.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash -i</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Hace que bash actúe como si hubiera sido invocado como una shell de login.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash -l</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Inicia una shell restringida (restricted shell).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash -r</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Lee comandos desde la entrada estándar (stdin).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">echo "ls" | bash -s</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Imprime las líneas de entrada de la shell a medida que se leen (verbose).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash -v script.sh</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-x</td>
        <td style="padding: 10px 15px;">Imprime comandos y sus argumentos a medida que se ejecutan (trace).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash -x script.sh</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">--norc</td>
        <td style="padding: 10px 15px;">No lee ni ejecuta el archivo de inicialización ~/.bashrc.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash --norc</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">--noprofile</td>
        <td style="padding: 10px 15px;">No lee los archivos de inicio del sistema ni del usuario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash --noprofile</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la información de la versión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bash --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">⛓️ CMD xargs</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Construir y ejecutar comandos desde stdin</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-0</td>
        <td style="padding: 10px 15px;">Los elementos de entrada terminan en carácter nulo (\0). Ideal para nombres con espacios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">find -print0 | xargs -0</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Lee los elementos desde un archivo en lugar de stdin.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -a lista.txt rm</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Especifica un delimitador de entrada personalizado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -d"\n"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-E</td>
        <td style="padding: 10px 15px;">Establece un marcador de fin de archivo (eof).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -E "STOP"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-I</td>
        <td style="padding: 10px 15px;">Reemplaza las ocurrencias de una cadena por los argumentos de entrada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ls | xargs -I {} cp {} /tmp</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Utiliza como máximo N líneas no vacías por línea de comandos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -L 1 echo</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Utiliza como máximo N argumentos por línea de comandos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -n 2 echo</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Pide confirmación antes de ejecutar cada comando.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -p rm</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">Ejecuta hasta N procesos simultáneamente (paralelismo).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -P 4</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">No ejecuta el comando si la entrada estándar está vacía.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -r rm</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Usa como máximo N caracteres por línea de comandos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -s 2048</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Imprime el comando en stderr antes de ejecutarlo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -t ls</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-x</td>
        <td style="padding: 10px 15px;">Termina si se excede el tamaño máximo (usar con -s).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xargs -x</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔀 CMD tr</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Traducir, comprimir o eliminar caracteres</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Usa el complemento del conjunto de caracteres (lo que NO está en el set).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tr -c "a" "b"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-C</td>
        <td style="padding: 10px 15px;">Igual que -c, pero basado en valores de caracteres, no bits.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tr -C [:alnum:]</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Elimina los caracteres indicados en el conjunto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tr -d "0-9"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Comprime secuencias de caracteres repetidos en una sola ocurrencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tr -s " "</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Trunca el primer conjunto a la longitud del segundo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tr -t "abcd" "12"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tr --help</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #4a4a4a, #1a1a1a); border-bottom: 2px solid #888;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #bbb; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔄 CMD exec</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Reemplazar procesos o redireccionar descriptores</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Pasa el nombre especificado como el argumento cero (argv[0]) del comando.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">exec -a nombre ls</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Ejecuta el comando con un entorno (environment) vacío.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">exec -c env</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Añade un guion al inicio del argumento cero (como una shell de login).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">exec -l bash</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">--</td>
        <td style="padding: 10px 15px;">Indica el fin de las opciones de exec.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">exec -- comando</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">┬ CMD tee</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Bifurcar la salida a archivos y pantalla</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Añade (append) a los archivos indicados en lugar de sobrescribirlos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ls | tee -a log.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Ignora las señales de interrupción (SIGINT).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tee -i file.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Diagnostica errores al escribir en salidas que no sean pipes.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tee -p file.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--output-error</td>
        <td style="padding: 10px 15px;">Define el comportamiento ante errores (warn, warn-nopipe, exit, exit-nopipe).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tee --output-error=warn</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tee --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tee --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">0x CMD xxd</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Generar volcados hexadecimales o revertirlos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Autoskip: oculta líneas de ceros duplicadas sustituyéndolas por un "*".</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -a file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Muestra el volcado en formato binario (bits) en lugar de hexadecimal.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -b file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Define el número de columnas (bytes por línea). Por defecto 16.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -c 8 file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Muestra en formato little-endian (cambia el orden de bytes en las palabras).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -e file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-g</td>
        <td style="padding: 10px 15px;">Agrupa bytes en grupos de N tamaño. Por defecto 2.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -g 1 file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Salida en formato de array de C (útil para incluir binarios en código).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -i image.png</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Muestra únicamente N bytes del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -l 64 file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Plain dump: salida continua de hexadecimal sin columnas ni ASCII.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -p file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Reverso: convierte un volcado hexadecimal de nuevo a binario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -r hex.txt bin.file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Salta N bytes desde el inicio del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -s 0x100 file.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Usa mayúsculas para las letras hexadecimales (A-F).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -u file.bin</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🎨 CMD ghex</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Editor hexadecimal gráfico (GNOME Hex Editor)</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra las opciones de ayuda de la aplicación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ghex --help</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--version</td>
        <td style="padding: 10px 15px;">Muestra la versión instalada de GHex.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ghex --version</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🧽 CMD sponge</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Absorber stdin y escribir al archivo tras el cierre</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Modo Append. Añade el contenido al final del archivo en lugar de sobrescribir.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">grep "err" log | sponge -a out</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda básica del comando.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sponge --help</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #008b8b, #1a1a1a); border-bottom: 2px solid #00cccc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #00cccc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔑 CMD ssh-keygen</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Generación y gestión de claves SSH</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Especifica el número de bits de la clave a crear.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -b 4096</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Especifica el tipo de clave (rsa, ed25519, ecdsa).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -t ed25519</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-C</td>
        <td style="padding: 10px 15px;">Añade un comentario a la clave (normalmente el email).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -C "user@mail.com"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Especifica el nombre de archivo de la clave generada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -f my_key</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-N</td>
        <td style="padding: 10px 15px;">Proporciona la nueva frase de paso (passphrase).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -N "pass"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Solicita cambiar la frase de paso de una clave existente.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -p -f id_rsa</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-y</td>
        <td style="padding: 10px 15px;">Lee una clave privada y muestra la clave pública en stdout.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -y -f key</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-R</td>
        <td style="padding: 10px 15px;">Elimina todas las claves de un host del archivo known_hosts.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -R 1.1.1.1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Muestra la huella digital (fingerprint) del archivo de clave.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -l -f key</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #00cccc; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Exporta claves a otros formatos (RFC4716, PKCS8, PEM).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ssh-keygen -e -f key</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔌 CMD ncat</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Navaja suiza de redes TCP/UDP (Nmap Project)</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Modo escucha (listen) para conexiones entrantes.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -l 4444</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Especifica el puerto de origen o el puerto a escuchar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -l -p 8080</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Usa el protocolo UDP en lugar de TCP.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -u target 53</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso; muestra detalles de la conexión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -v google.com 80</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Ejecuta un programa tras la conexión (Bind/Reverse Shell).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -l -e /bin/bash</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">--ssl</td>
        <td style="padding: 10px 15px;">Establece la conexión utilizando cifrado SSL/TLS.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat --ssl -l 443</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-k</td>
        <td style="padding: 10px 15px;">Mantiene la conexión abierta tras una desconexión (Keep-open).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -l -k 4444</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-z</td>
        <td style="padding: 10px 15px;">Modo Zero-I/O: solo comprueba si el puerto está abierto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -z 1.1.1.1 80</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">--allow</td>
        <td style="padding: 10px 15px;">Permite únicamente las IPs especificadas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -l --allow IP</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Establece un tiempo de espera (timeout) para la conexión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">ncat -w 10 IP 80</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📊 CMD wc</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Contador de palabras, líneas y bytes (Word Count)</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Imprime el conteo de bytes.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">wc -c file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Imprime el conteo de caracteres (considera codificación multi-byte).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">wc -m file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Imprime el conteo de líneas (saltos de línea).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">wc -l file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Imprime la longitud de la línea más larga del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">wc -L file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Imprime el conteo de palabras.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">wc -w file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--help</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">wc --help</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD diff</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Comparación detallada de archivos</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td><td>Trata todos los archivos como texto.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -a bin1 bin2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td><td>Ignora cambios en la cantidad de espacios en blanco.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -b f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-B</td><td>Ignora cambios que solo insertan o borran líneas vacías.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -B f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td><td>Usa el formato de salida con contexto (3 líneas).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -c f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td><td>Intenta encontrar un conjunto de cambios más pequeño.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -d f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-e</td><td>Genera un script para el editor 'ed'.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -e f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td><td>Ignora mayúsculas y minúsculas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -i f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-q</td><td>Modo breve; solo indica si los archivos difieren.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -q f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r</td><td>Compara directorios de forma recursiva.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -r dir1 dir2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td><td>Informa cuando dos archivos son idénticos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -s f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-u</td><td>Usa el formato de salida unificado (típico para parches).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -u f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-w</td><td>Ignora todos los espacios en blanco al comparar líneas.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -w f1 f2</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-y</td><td>Muestra la salida en dos columnas (side-by-side).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">diff -y f1 f2</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔑 CMD ssh</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Acceso y ejecución remota segura</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-1 / -2</td><td>Fuerza el uso de la versión 1 o 2 del protocolo SSH.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -2 user@host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-4 / -6</td><td>Fuerza el uso de direcciones IPv4 o IPv6 únicamente.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -4 user@host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-A / -a</td><td>Habilita / Deshabilita el reenvío del agente de autenticación.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -A user@host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-C</td><td>Solicita compresión de todos los datos enviados.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -C user@host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-D</td><td>Redirección dinámica de puertos (SOCKS proxy).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -D 8080 host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-f</td><td>Pasa SSH a segundo plano justo antes de la ejecución del comando.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -f host cmd</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-G</td><td>Muestra la configuración de SSH para el host tras evaluar opciones.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -G host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-i</td><td>Especifica el archivo de identidad (clave privada).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -i ~/.ssh/id_rsa</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-L</td><td>Redirección de puerto local hacia el remoto.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -L 80:host:80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-N</td><td>No ejecuta ningún comando remoto (útil solo para túneles).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -N -L 80:h:80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-p</td><td>Puerto en el que se conecta al servidor remoto.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -p 2222 host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-R</td><td>Redirección de puerto remoto hacia el local.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -R 8080:localhost:80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-v / -vv / -vvv</td><td>Modo verboso para depuración (niveles del 1 al 3).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -v host</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-X / -Y</td><td>Habilita el reenvío de X11 (seguro / inseguro).</td><td style="padding: 10px 15px;"><code style="color: #aaa;">ssh -X user@host</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔌 CMD nc</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Lectura y escritura en red (Netcat)</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-4 / -6</td><td>Fuerza el uso de IPv4 o IPv6.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -4 google.com 80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-d</td><td>No intenta leer desde stdin.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -d target 4444</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-i</td><td>Intervalo de espera entre líneas enviadas o puertos escaneados.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -i 1 target 80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-k</td><td>Mantiene el socket de escucha abierto tras una desconexión.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -lk 4444</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-l</td><td>Modo de escucha para conexiones entrantes.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -l 4444</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-n</td><td>No realiza resolución DNS de los nombres de host.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -n 1.1.1.1 80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-p</td><td>Especifica el puerto local a utilizar.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -p 1234 target 80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-u</td><td>Usa el protocolo UDP en lugar de TCP.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -u target 53</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-v</td><td>Modo verboso; da más detalles de la conexión.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -v target 80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-w</td><td>Establece un timeout para las conexiones.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -w 5 target 80</code></td></tr>
      <tr style="border-bottom: 1px solid #2a2a2a;"><td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-z</td><td>Escaneo de puertos: no envía datos, solo busca puertos abiertos.</td><td style="padding: 10px 15px;"><code style="color: #aaa;">nc -zv target 1-100</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📝 CMD sed</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Editor de flujo para transformación de texto</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Modo silencioso. No imprime las líneas automáticamente (útil con comando 'p').</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -n '5p' file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Añade scripts o comandos para ser ejecutados.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -e 's/a/b/' -e 's/c/d/'</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Añade el contenido de un archivo de script a los comandos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -f script.sed file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Edición "in-place". Sobrescribe el archivo original con los cambios.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -i 's/old/new/g' f</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-r / -E</td>
        <td style="padding: 10px 15px;">Habilita el uso de expresiones regulares extendidas (ERE).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -E 's/(a|b)/c/'</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Trata los archivos de entrada como flujos separados en lugar de uno solo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -s 's/a/b/' f1 f2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Modo unbuffered. Vacía la salida con más frecuencia.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -u 's/x/y/'</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-z</td>
        <td style="padding: 10px 15px;">Usa el carácter nulo (\0) como separador de líneas.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">sed -z 's/a/b/'</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📊 CMD stat</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Mostrar estado detallado de archivos/directorios</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Sigue enlaces simbólicos (dereference).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">stat -L link</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Muestra el estado del sistema de archivos en lugar del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">stat -f /</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Especifica un formato de salida personalizado (format).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">stat -c %a file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--printf</td>
        <td style="padding: 10px 15px;">Similar a -c, pero interpreta secuencias de escape de barra invertida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">stat --printf="%n\n"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Modo conciso (terse). Imprime la información de forma resumida en una línea.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">stat -t file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📁 CMD mktemp</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Crear archivos o directorios temporales de forma segura</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Crea un directorio temporal en lugar de un archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mktemp -d</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Modo dry-run. No crea nada, solo imprime el nombre que usaría (inseguro).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mktemp -u</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Modo silencioso. Suprime mensajes de error sobre fallos en la creación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mktemp -q</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Usa el directorio especificado como base para el temporal.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mktemp -p /tmp</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-t</td>
        <td style="padding: 10px 15px;">Genera una plantilla basada en el nombre indicado (obsoleto, usar plantillas directamente).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mktemp -t my.XXXX</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--tmpdir</td>
        <td style="padding: 10px 15px;">Interpreta el primer argumento como directorio base (equivalente a -p).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">mktemp --tmpdir=/tmp</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🔍 CMD grep</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Búsqueda de patrones mediante expresiones regulares</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td><td>Ignora la distinción entre mayúsculas y minúsculas.</td><td><code style="color: #aaa;">grep -i "error"</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-v</td><td>Invierte la búsqueda: muestra las líneas que NO coinciden.</td><td><code style="color: #aaa;">grep -v "info"</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td><td>Muestra solo el número total de líneas coincidentes.</td><td><code style="color: #aaa;">grep -c "bash"</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-l</td><td>Muestra solo los nombres de los archivos con coincidencias.</td><td><code style="color: #aaa;">grep -l "main" *.c</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-n</td><td>Muestra el número de línea de cada coincidencia.</td><td><code style="color: #aaa;">grep -n "TODO"</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r / -R</td><td>Búsqueda recursiva en directorios.</td><td><code style="color: #aaa;">grep -r "pwd" /etc</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-w</td><td>Busca solo palabras completas.</td><td><code style="color: #aaa;">grep -w "lib"</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-x</td><td>Busca coincidencias que ocupen la línea completa.</td><td><code style="color: #aaa;">grep -x "exacta"</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-A / -B</td><td>Muestra N líneas Después (After) o Antes (Before) de la coincidencia.</td><td><code style="color: #aaa;">grep -A 2 "id"</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-C</td><td>Muestra N líneas de contexto (antes y después).</td><td><code style="color: #aaa;">grep -C 3 "err"</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-E</td><td>Interpreta el patrón como Expresión Regular Extendida (ERE).</td><td><code style="color: #aaa;">grep -E "a|b"</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-F</td><td>Trata el patrón como una cadena fija (Fixed strings), no regex.</td><td><code style="color: #aaa;">grep -F ".*"</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-o</td><td>Muestra únicamente la parte de la línea que coincide.</td><td><code style="color: #aaa;">grep -o "[0-9]*"</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-q</td><td>Modo silencioso (Quiet); no escribe nada, solo devuelve status.</td><td><code style="color: #aaa;">grep -q "test" f</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🌱 CMD git</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Gestión de control de versiones</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción / Cmd</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-C</td><td>Ejecuta git como si se hubiera iniciado en la ruta especificada.</td><td><code style="color: #aaa;">git -C /ruta status</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-c</td><td>Pasa un parámetro de configuración a la ejecución.</td><td><code style="color: #aaa;">git -c user.name=X</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">add</td><td>Añade contenido de archivos al índice (staging area).</td><td><code style="color: #aaa;">git add .</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">commit</td><td>Registra los cambios en el repositorio.</td><td><code style="color: #aaa;">git commit -m "msg"</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">push</td><td>Actualiza referencias remotas junto con objetos asociados.</td><td><code style="color: #aaa;">git push origin main</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">pull</td><td>Incorpora cambios de un repo remoto en la rama actual.</td><td><code style="color: #aaa;">git pull</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">fetch</td><td>Descarga objetos y referencias de otro repositorio.</td><td><code style="color: #aaa;">git fetch</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">status</td><td>Muestra el estado del árbol de trabajo.</td><td><code style="color: #aaa;">git status</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">branch</td><td>Lista, crea o borra ramas.</td><td><code style="color: #aaa;">git branch -d feat</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">checkout</td><td>Cambia de rama o restaura archivos del árbol de trabajo.</td><td><code style="color: #aaa;">git checkout rama</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">log</td><td>Muestra los registros de confirmación (commits).</td><td><code style="color: #aaa;">git log --oneline</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--version</td><td>Muestra la versión de git instalada.</td><td><code style="color: #aaa;">git --version</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">✂️ CMD cut</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Extraer fragmentos de líneas de texto</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td><td>Selecciona solo los bytes especificados.</td><td><code style="color: #aaa;">cut -b 1-10 file</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td><td>Selecciona solo los caracteres especificados.</td><td><code style="color: #aaa;">cut -c 5,10</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-d</td><td>Define el delimitador que separa los campos (por defecto es TAB).</td><td><code style="color: #aaa;">cut -d ":" -f 1</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-f</td><td>Selecciona únicamente los campos (fields) especificados.</td><td><code style="color: #aaa;">cut -f 2,4</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td><td>No imprime líneas que no contengan el delimitador.</td><td><code style="color: #aaa;">cut -d "," -f 1 -s</code></td></tr>
      <tr style="background-color: #202020;"><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--complement</td><td>Extrae el complemento de la selección (lo que NO se eligió).</td><td><code style="color: #aaa;">cut -f 1 --complement</code></td></tr>
      <tr><td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">--output-delimiter</td><td>Cambia el delimitador en la salida.</td><td><code style="color: #aaa;">cut -d: -f1 --out-d=" "</code></td></tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📂 CMD cd</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Cambiar el directorio de trabajo actual</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Fuerza el seguimiento de enlaces simbólicos (comportamiento lógico).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cd -L /var/www</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-P</td>
        <td style="padding: 10px 15px;">Usa la estructura de directorios física en lugar de seguir enlaces simbólicos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cd -P /var/www</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-</td>
        <td style="padding: 10px 15px;">Cambia al directorio de trabajo anterior ($OLDPWD).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cd -</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">~</td>
        <td style="padding: 10px 15px;">Cambia al directorio personal del usuario ($HOME).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">cd ~</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">✨ CMD js-beautify</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Formateador de código JavaScript / JSON</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Reemplaza el archivo original con la versión formateada.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">js-beautify -r file.js</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Tamaño de la indentación (número de espacios).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">js-beautify -s 2</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Carácter de indentación (espacio por defecto).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">js-beautify -c " "</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Conserva las líneas nuevas originales.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">js-beautify -p script.js</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Archivo de entrada a formatear.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">js-beautify -f test.js</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Añade una línea nueva al final del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">js-beautify -n file.js</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-X</td>
        <td style="padding: 10px 15px;">No imprime la salida (útil con -r).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">js-beautify -r -X *.js</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #e67e22, #1a1a1a); border-bottom: 2px solid #ff944d;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff944d; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🌐 CMD curl</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Transferencia de datos con URLs</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-o</td>
        <td style="padding: 10px 15px;">Escribe la salida en un archivo en lugar de stdout.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -o out.html url</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-O</td>
        <td style="padding: 10px 15px;">Escribe la salida en un archivo local con el mismo nombre que el remoto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -O url/file.zip</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Sigue las redirecciones HTTP (301, 302).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -L bit.ly/abc</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Incluye las cabeceras HTTP de respuesta en la salida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -i example.com</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-I</td>
        <td style="padding: 10px 15px;">Obtiene únicamente las cabeceras HTTP (método HEAD).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -I example.com</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-X</td>
        <td style="padding: 10px 15px;">Especifica el método de petición (GET, POST, DELETE, etc.).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -X POST url</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-H</td>
        <td style="padding: 10px 15px;">Añade una cabecera personalizada a la petición.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -H "Auth: 123" url</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Autenticación de usuario (usuario:contraseña).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -u user:pass url</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Envía datos en una petición POST.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -d "id=1" url</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-k</td>
        <td style="padding: 10px 15px;">Permite conexiones SSL "inseguras" (ignora certificados).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -k https://site</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff944d; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Modo silencioso. No muestra barra de progreso ni errores.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">curl -s url</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🐧 CMD awk</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Procesamiento y reporte de texto</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-F</td>
        <td style="padding: 10px 15px;">Define el separador de campos (Field Separator).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">awk -F: '{print $1}'</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Asigna un valor a una variable de awk antes de ejecutar el programa.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">awk -v n=5 '{print n}'</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Lee el programa awk desde un archivo en lugar de la línea de comandos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">awk -f script.awk data</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">--posix</td>
        <td style="padding: 10px 15px;">Fuerza que awk siga estrictamente el estándar POSIX.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">awk --posix -f s.awk</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-W</td>
        <td style="padding: 10px 15px;">Opciones específicas de la implementación (ej: lint para avisos).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">awk -W lint '{...}'</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🧮 CMD bc</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Lenguaje de calculadora de precisión arbitraria</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Muestra el uso (ayuda) y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bc -h</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Fuerza el modo interactivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bc -i</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Carga la librería matemática predefinida (define funciones trigonométricas, etc.) y fija 'scale' a 20.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bc -l</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">No imprime el mensaje de bienvenida de GNU bc (modo 'quiet').</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bc -q</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Habilita el cumplimiento estricto del lenguaje POSIX bc.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bc -s</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Muestra avisos (warnings) para extensiones de GNU a POSIX bc.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bc -w</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Imprime el número de versión y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">bc -v</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #ff66b2, #1a1a1a); border-bottom: 2px solid #ff99cc;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #ff99cc; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🐍 CMD python3</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Intérprete del lenguaje Python 3</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Ejecuta el código Python pasado como cadena de texto.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -c "print(1)"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Ejecuta un módulo como script (ej. http.server, pip, venv).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -m http.server</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Entra en modo interactivo tras ejecutar un script.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -i script.py</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-O</td>
        <td style="padding: 10px 15px;">Optimiza el bytecode (elimina 'assert' y __debug__).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -O script.py</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-OO</td>
        <td style="padding: 10px 15px;">Igual que -O, pero también elimina los docstrings.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -OO script.py</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Activa la salida de depuración del analizador (parser).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -d script.py</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-E</td>
        <td style="padding: 10px 15px;">Ignora todas las variables de entorno de Python (PYTHONPATH, etc.).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -E</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">No añade el directorio de paquetes de usuario al sys.path.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -s</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-S</td>
        <td style="padding: 10px 15px;">No carga el módulo 'site' al inicio.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -S</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Modo verboso. Muestra mensajes cada vez que se carga un módulo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -v</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Usa salida sin búfer (unbuffered) para stdout y stderr.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -u</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-W</td>
        <td style="padding: 10px 15px;">Control de avisos (warnings). ej: -W ignore, -W error.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -W error</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-X</td>
        <td style="padding: 10px 15px;">Opciones específicas de la implementación.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -X faulthandler</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-V</td>
        <td style="padding: 10px 15px;">Imprime la versión de Python y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -V</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #ff99cc; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">No imprime mensajes de versión y copyright en modo interactivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">python3 -q</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #4a4a4a, #1a1a1a); border-bottom: 2px solid #888;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #bbb; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🆔 CMD pwdx</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Reportar el directorio de trabajo de un proceso</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.9em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-V</td>
        <td style="padding: 10px 15px;">Imprime la versión del programa y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">pwdx -V</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Muestra la ayuda y sale.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">pwdx -h</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">[PID]</td>
        <td style="padding: 10px 15px;">El argumento principal es el ID del proceso a investigar (soporta múltiples).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">pwdx 1234 5678</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">📡 CMD tcpdump</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Analizador de tráfico de red</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Especifica la interfaz de red (any para todas).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -i eth0</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Captura solo N paquetes y luego se detiene.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -c 100</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">No convierte direcciones (IP, puertos) en nombres.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -n</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-v / -vv / -vvv</td>
        <td style="padding: 10px 15px;">Niveles crecientes de verbosidad en la salida.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -vv</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Escribe los paquetes crudos en un archivo (pcap).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -w log.pcap</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Lee paquetes desde un archivo guardado con -w.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -r log.pcap</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-A</td>
        <td style="padding: 10px 15px;">Imprime cada paquete en formato ASCII (útil para ver texto plano).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -A</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-X</td>
        <td style="padding: 10px 15px;">Muestra el contenido del paquete en Hex y ASCII.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -X</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Tamaño del paquete a capturar (Snaplen). 0 es el máximo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -s 0</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-D</td>
        <td style="padding: 10px 15px;">Lista todas las interfaces de red disponibles para capturar.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -D</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Lista los tipos de enlace de datos de la interfaz.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -L</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Salida rápida. Muestra menos información de protocolo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tcpdump -q</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #004182, #1a1a1a); border-bottom: 2px solid #0056b3;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #4da3ff; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">0x CMD xxd</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Herramienta de volcado Hexadecimal</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Autoskip: reemplaza líneas de ceros por un asterisco.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -a binary.bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-b</td>
        <td style="padding: 10px 15px;">Muestra el volcado en formato binario (bits).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -b file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Define el número de columnas (bytes por línea).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -c 8 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Formato little-endian (cambia el orden de bytes).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -e file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-g</td>
        <td style="padding: 10px 15px;">Agrupa los bytes en grupos de N tamaño.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -g 1 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Salida en formato de array de lenguaje C.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -i image.png</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-l</td>
        <td style="padding: 10px 15px;">Muestra únicamente N bytes del archivo.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -l 32 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Modo "Plain": solo texto hexadecimal sin formato.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -p file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Operación inversa: convierte el hex de nuevo a binario.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -r hex.txt bin</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-s</td>
        <td style="padding: 10px 15px;">Empieza el volcado con un offset de N bytes.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -s 0x100 file</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #4da3ff; font-weight: bold;">-u</td>
        <td style="padding: 10px 15px;">Usa mayúsculas para las letras hexadecimales.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">xxd -u file</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🦈 CMD tshark</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Analizador de protocolos de red (Terminal Wireshark)</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-i</td>
        <td style="padding: 10px 15px;">Establece la interfaz de captura.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -i wlan0</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-f</td>
        <td style="padding: 10px 15px;">Filtro de captura (formato libpcap).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -f "tcp port 80"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-Y</td>
        <td style="padding: 10px 15px;">Filtro de visualización (formato Wireshark).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -Y "http.request"</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-w</td>
        <td style="padding: 10px 15px;">Guarda la captura en un archivo .pcapng.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -w sniff.pcap</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Lee y analiza un archivo de captura.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -r capture.pcap</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-T</td>
        <td style="padding: 10px 15px;">Define el formato de salida (fields, json, psml, text).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -T json</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-e</td>
        <td style="padding: 10px 15px;">Extrae campos específicos (usar con -T fields).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -T fields -e ip.src</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-z</td>
        <td style="padding: 10px 15px;">Genera estadísticas variadas (endpoints, protocolos, etc.).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -z io,phs</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-V</td>
        <td style="padding: 10px 15px;">Muestra los paquetes con todos los detalles (Verbose).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -V</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Condición de parada (duration:N, filesize:N, files:N).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">tshark -a duration:10</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #4a4a4a, #1a1a1a); border-bottom: 2px solid #888;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #bbb; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🚫 CMD disown</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Desasociar procesos de la shell</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Afecta a todos los trabajos actuales si no se especifica ID.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">disown -a</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Mantiene el trabajo en la tabla pero evita que reciba SIGHUP al cerrar la shell.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">disown -h %1</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Afecta solo a los trabajos que están en ejecución (running).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">disown -r</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #bbb; font-weight: bold;">[%ID]</td>
        <td style="padding: 10px 15px;">El número del trabajo indicado en la lista de 'jobs'.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">disown %2</code></td>
      </tr>
    </tbody>
  </table>
</div>

<div style="background-color: #1a1a1a; border-radius: 12px; padding: 1px; border: 1px solid #333; overflow: hidden; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;">
  <table style="border-collapse: collapse; width: 100%; color: #d1d1d1;">
    <thead>
      <tr style="background: linear-gradient(to right, #1a5d1a, #1a1a1a); border-bottom: 2px solid #2eb82e;">
        <th colspan="3" style="padding: 18px 15px; text-align: left;">
          <span style="color: #2eb82e; font-family: monospace; font-size: 1.4em; font-weight: bold; text-shadow: 1px 1px 2px rgba(0,0,0,0.5);">🛡️ CMD msfconsole</span>
          <span style="color: #888; font-size: 0.85em; margin-left: 12px; font-weight: normal; border-left: 1px solid #444; padding-left: 12px;">Consola del Framework Metasploit</span>
        </th>
      </tr>
      <tr style="background-color: #252525; color: #888; font-size: 0.75em; text-transform: uppercase; letter-spacing: 1px;">
        <th style="padding: 10px 15px; text-align: left; width: 20%;">Opción</th>
        <th style="padding: 10px 15px; text-align: left; width: 55%;">Descripción</th>
        <th style="padding: 10px 15px; text-align: left; width: 25%;">Ejemplo</th>
      </tr>
    </thead>
    <tbody style="font-size: 0.85em;">
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-a</td>
        <td style="padding: 10px 15px;">Pregunta antes de salir de Metasploit o usa --confirm-exit.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -a</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-c</td>
        <td style="padding: 10px 15px;">Carga el archivo de configuración especificado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -c config.xml</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-d</td>
        <td style="padding: 10px 15px;">Habilita el modo de depuración (Debug).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -d</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-E</td>
        <td style="padding: 10px 15px;">Establece el entorno de Rails a producción (por defecto es desarrollo).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -E production</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-h</td>
        <td style="padding: 10px 15px;">Muestra el mensaje de ayuda con todas las opciones.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -h</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-m</td>
        <td style="padding: 10px 15px;">Carga un directorio de módulos adicional.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -m ./extra</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-n</td>
        <td style="padding: 10px 15px;">Desactiva el uso de la base de datos.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -n</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-o</td>
        <td style="padding: 10px 15px;">Escribe la salida en el archivo especificado.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -o log.txt</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-p</td>
        <td style="padding: 10px 15px;">Carga un plugin al iniciar (ej. Nessus, OpenVAS).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -p alias</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-q</td>
        <td style="padding: 10px 15px;">Modo silencioso. No muestra el banner de inicio.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -q</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-r</td>
        <td style="padding: 10px 15px;">Ejecuta un archivo de script (recurso) con comandos secuenciales.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -r script.rc</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-v</td>
        <td style="padding: 10px 15px;">Muestra la información de versión.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -v</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-x</td>
        <td style="padding: 10px 15px;">Ejecuta los comandos de consola indicados (separados por ';').</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -x "use exploit/..."</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">-L</td>
        <td style="padding: 10px 15px;">Carga las librerías locales de Ruby (load path).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole -L</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">--no-readline</td>
        <td style="padding: 10px 15px;">Desactiva el soporte de Readline (útil para terminales simples).</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole --no-readline</code></td>
      </tr>
      <tr style="border-bottom: 1px solid #2a2a2a; background-color: #202020;">
        <td style="padding: 10px 15px; font-family: monospace; color: #2eb82e; font-weight: bold;">--real-readline</td>
        <td style="padding: 10px 15px;">Fuerza el uso de la librería Readline real del sistema.</td>
        <td style="padding: 10px 15px;"><code style="color: #aaa;">msfconsole --real-readline</code></td>
      </tr>
    </tbody>
  </table>
</div>
