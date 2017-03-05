package me.dreksbr.dtext;

import java.io.File;
import java.util.List;

import org.bukkit.ChatColor;
import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.player.PlayerJoinEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class Drek extends JavaPlugin implements Listener {

	@Override
	public void onEnable() {
		File file = new File(getDataFolder(), "config.yml");
		if (!file.exists()) {
			getServer().getConsoleSender().sendMessage("§2[TestecomGui] Config nao encontrada");
			getServer().getConsoleSender().sendMessage("§2[TestecomGui] Criando nova config...");
			getServer().getConsoleSender().sendMessage("§2[TestecomGui] Config criada com sucesso");
			saveDefaultConfig();
		}
		getServer().getPluginManager().registerEvents(this, this);
		getServer().getConsoleSender().sendMessage("§2[DText] Ligado");
		getServer().getConsoleSender().sendMessage("§2[DText] Author: DreksBr");
	}

	@Override
	public void onDisable() {
		saveConfig();
		getServer().getConsoleSender().sendMessage("§c[DText] Desligado");
	}

	@Override
	public boolean onCommand(CommandSender sender, Command command, String label, String[] args) {
		if (command.getName().equalsIgnoreCase("site")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Player");
				return true;
			}
			List<String> s = getConfig().getStringList("Site");
			Player p = (Player) sender;
			for (String site : s) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', site));
			}
		}
		if (command.getName().equalsIgnoreCase("ajuda")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Player");
				return true;
			}
			List<String> aj = getConfig().getStringList("Ajuda");
			Player p = (Player) sender;
			for (String ajuda : aj) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', ajuda));
			}
		}
		if (command.getName().equalsIgnoreCase("regras")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Players");
				return true;
			}
			List<String> re = getConfig().getStringList("Regras");
			Player p = (Player) sender;
			for (String regras : re) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', regras));
			}
		}
		if (command.getName().equalsIgnoreCase("vip")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Players");
				return true;
			}
			List<String> vp = getConfig().getStringList("Vip");
			Player p = (Player) sender;
			for (String vip : vp) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', vip));
			}
		}
		if (command.getName().equalsIgnoreCase("eventos")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Players");
				return true;
			}
			List<String> event = getConfig().getStringList("Eventos");
			Player p = (Player) sender;
			for (String eventos : event) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', eventos));
			}
		}
		if (command.getName().equalsIgnoreCase("youtuber")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Players");
				return true;
			}
			List<String> yt = getConfig().getStringList("YouTuber");
			Player p = (Player) sender;
			for (String youtuber : yt) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', youtuber));
			}
		}
		if (command.getName().equalsIgnoreCase("cores")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Players");
				return true;
			}
			List<String> cs = getConfig().getStringList("Cores");
			Player p = (Player) sender;
			for (String cores : cs) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', cores));
			}
		}
		if (command.getName().equalsIgnoreCase("terrenos")) {
			if (!(sender instanceof Player)) {
				sender.sendMessage("Apenas Players");
				return true;
			}
			List<String> tr = getConfig().getStringList("Terrenos");
			Player p = (Player) sender;
			for (String terrenos : tr) {
				p.sendMessage(ChatColor.translateAlternateColorCodes('&', terrenos));
			}
		}
		if (command.getName().equalsIgnoreCase("dtext")) {
			if (!sender.hasPermission("dtext.reload")) {
				sender.sendMessage("§cSem Permição");
				return true;
			}
			if (args.length == 0) {
				sender.sendMessage("§cERRO §7Use /dtext reload");
				return true;
			}
			if (args[0].equalsIgnoreCase("reload")) {
				reloadConfig();
				sender.sendMessage("§a[DText] Config Recarregada com sucesso");
			}
		}
		return false;
	}

	@EventHandler
	public void onJoinDEV(PlayerJoinEvent e) {
		if ((e.getPlayer().getName().equalsIgnoreCase("DreksBr"))) {
			e.getPlayer().sendMessage("§aEsse servidor usa seu plugin: §f" + getDescription().getName());
		}
	}
}
