About Me:
```zig
const std = @import("std");
const rand = std.crypto.random;

// Hi! I'm Karvie
const Karvie = struct {
    home_address: []const u8,
    cool_shit: []const u8,
    literal_art: []const u8,
    novels: []const u8,
};

// Welcome to my GitHub!
pub fn main() void {
    
    // This is me
    const me = Karvie{
        .home_address =
        \\ https://github.com/Karvie0
        \\ https://youtube.com/@karvie
        \\ https://x.com/Karvie0
        ,
        .cool_shit =
        \\ blender
        \\ linux
        \\ anime
        \\ zig
        \\ blender
        ,
        .literal_art =
        \\ Nichijou
        \\ Space Patrol Luluco
        \\ Inferno Cop
        \\ Suzume
        \\ Dungeon Meshi
        ,
        .novels =
        \\ Nichijou - Keiichi Arawi
        \\ CITY - Keiichi Arawi
        \\ Tensura - Fuse
        \\ The Bible - Various
        ,
    };
    
    // It's not so fun to read about me as code...
    // Let's print me to the console!
    
    // First we'll put my pieces together
    var buffer: [300]u8 = undefined;
    const used = concat(&[_][]const u8{
        me.home_address,
        me.cool_shit,
        me.literal_art,
        me.novels,
    },
        &buffer
    );
    
    // I love blender
    blender(buffer[0..used]);
    
    // And print!
    std.debug.print("Hi! I like {s}\n", .{buffer[0..used]});
}

fn concat(strings: []const []const u8, buffer: []u8) usize {
    var buffer_used: usize = 0;
    for (strings) |string| {
        if (buffer_used + string.len < buffer.len + 1) {
            @memcpy(buffer[buffer_used..buffer_used+string.len], string);
        } else unreachable;
        
        buffer_used += string.len;
    }
    return buffer_used;
}

fn blender(buffer: []u8) void {
    for (0..2) |_| {
        for(0..buffer.len) |i| {
            const rand_i: usize = rand.int(usize) % (buffer.len - 1);
            buffer[i] ^= buffer[rand_i];
            buffer[rand_i] ^= buffer[i];
            buffer[i] ^= buffer[rand_i];
        }
    }
}
```
