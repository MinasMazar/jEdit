require 'minitest/autorun'
require 'pescobells'

class TestPescobells < Minitest::Test

  include Pescobells

  def setup
    self.cli_audio_player = 'play'
  end

  def test_that_it_has_a_version_number
    refute_nil ::Pescobells::VERSION
  end

  def test_calculate_bells
    time = Time.now
    bells = time_to_bells time 
    assert_equal bells[0].size, time.hour % 12
    assert_equal bells[1].size, time.min / 15  
  end

  def test_playing_bells
    [ [12,31], [21,9], [16,49] ].each do |time|
      time = Time.new 2011,11,11,time[0], time[1]
      bells = time_to_bells time
      puts "\n*** Your should listen n. #{bells[0].size} hour bells, n. #{bells[1].size} quarter bells. ***\n"
      assert_equal [ true ],  play_bells(bells).uniq
      sleep 4
    end
  end

end
