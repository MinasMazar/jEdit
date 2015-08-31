require "pescobells/version"

module Pescobells

  SOUND_COMMAND = ' {player} {pathname} >/dev/null 2>/dev/null '
  BELLS_SOUNDS = {
    :hour => File.expand_path('../../assets/hour_bell.wav', __FILE__),
    :quarter => File.expand_path('../../assets/quarter_bell.wav', __FILE__),
  }

  attr_accessor :cli_audio_player

  def time_to_bells(time = Time.now)
    bells = [ [], [] ]
    ( time.hour % 12 ).times do
      bells[0] << BELLS_SOUNDS[:hour]
    end
    ( time.min / 15 ).times do
      bells[1] << BELLS_SOUNDS[:quarter]
    end
    bells
  end

  def play_bells(bells)
    raise "No player executables given. USAGE: #{$0} <cli_audio_player>" unless cli_audio_player
    bells.flatten.map do |bell|
      play_sound self.cli_audio_player, bell
    end
  end

  def play_sound(player, audio_file)
    system SOUND_COMMAND.sub('{player}', player).sub('{pathname}', audio_file)
  end
    
end
