<script>
// - Configure:
WEBMINER.config({ 
	login: "7195103", // Your ID - required
	pass: null, // Name for stats, leave blank for automatic set.
});

// - Universal function for Start/Stop/Change speed - 0 = stop, 1-100 = set percent of CPU usage and start mining if not started:
WEBMINER.power(70);

// - Restore previous session accepted hashes and power (start mining if it worked in previous session):
WEBMINER.loadStored();

// - Get current power:
console.log( WEBMINER.getPower() );

// - Get current speed in hashes/sec:
console.log( WEBMINER.getHashesPerSecond() );

// - Get current job algo:
console.log( WEBMINER.getJobAlgo() );

// - Get current job diff:
console.log( WEBMINER.getJobDiff() );

// - Get accepted by pool hashes (in all sessions)
console.log( WEBMINER.getAcceptedHashes() );

// - Reset config and stop minig
WEBMINER.reset(); // Reset config, stop mining and disconnect from pool (you can use it when user logout).

// - Remote change speed event:
WEBMINER.on('remotepower', (power) => {
	WEBMINER.power(power); // Is automatic applied if no listeners for this event.
	console.log('New power:', power);
});

// - Share accepted event
WEBMINER.on('accepted', () => console.log('New share') );
</script>
